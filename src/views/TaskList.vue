<template>
    <div>
      <h1>Lista de Tareas</h1>
      <!-- Botón para cargar tareas -->
      <button @click="fetchTasks">Cargar Tareas</button>
  
      <!-- Mostrar tareas cargadas -->
      <div v-if="tasks.length > 0">
        <div v-for="task in tasks" :key="task.id">
          <div>
            <!-- Tarea con estilo que cambia según si está completada o no -->
            <h5 :style="{ textDecoration: task.completed ? 'line-through' : 'none' }">
              {{ task.todo }}
            </h5>
            <span>{{ task.completed ? 'Completada' : 'Pendiente' }}</span>
  
            <!-- Botón para cambiar el estado de la tarea -->
            <button @click="toggleTaskCompletion(task)">
              {{ task.completed ? 'Desmarcar' : 'Completar' }}
            </button>
  
            <!-- Botón para eliminar la tarea -->
            <button @click="deleteTask(task)">Eliminar</button>
          </div>
        </div>
      </div>
      <!-- Mensaje cuando no hay tareas -->
      <div v-else>
        <p>No hay tareas disponibles. Haz clic en "Cargar Tareas" para obtenerlas.</p>
      </div>
    </div>
  </template>
  
  <script>
  // Importamos Axios para hacer solicitudes HTTP
  import axios from "axios";
  
  export default {
    name: "TaskList",
    data() {
      return {
        tasks: [], // Almacenamiento de las tareas obtenidas desde la API
      };
    },
    methods: {
      // Método para obtener las tareas desde la API
      async fetchTasks() {
        try {
          // Realizamos la solicitud a la API
          const response = await axios.get("https://dummyjson.com/todos");
          this.tasks = response.data.todos; // Asignamos las tareas obtenidas al array tasks
        } catch (error) {
          console.error("Error al cargar las tareas:", error);
        }
      },
  
      // Método para cambiar el estado de la tarea (completada/no completada)
      toggleTaskCompletion(task) {
        task.completed = !task.completed; // Cambiar el estado de completada
      },
  
      // Método para eliminar una tarea
      deleteTask(task) {
        // Filtramos las tareas para eliminar la seleccionada
        this.tasks = this.tasks.filter((t) => t.id !== task.id);
      },
    },
  };
  </script>
  
  <style scoped>
  /* Estilos básicos para la lista de tareas */
  button {
    margin: 5px;
  }
  
  h5 {
    display: inline-block;
    margin-right: 10px;
  }
  </style>
  