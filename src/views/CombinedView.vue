<template>
    <div>
      <h1>Lista de Tareas</h1>
  
      <!-- Componente para agregar tareas -->
      <AddTask @add-task="addTask" />
  
      <!-- Componente para mostrar las tareas -->
      <TaskList :tasks="tasks" @delete-task="deleteTask" />
  
      <button @click="fetchTasks">Cargar Tareas</button>
    </div>
  </template>
  
  <script>
  import axios from "axios";
  import AddTask from "./AddTask.vue";
  import TaskList from "./TaskList.vue";
  
  export default {
    name: "CombinedView",
    components: {
      AddTask,
      TaskList,
    },
    data() {
      return {
        tasks: [], // Para almacenar las tareas obtenidas de la API y las agregadas
      };
    },
    methods: {
      // Obtener tareas desde la API
      async fetchTasks() {
        try {
          const response = await axios.get("https://dummyjson.com/todos");
          this.tasks = response.data.todos; // Actualiza la lista de tareas
        } catch (error) {
          console.error("Error al cargar las tareas:", error);
        }
      },
  
      // Agregar una nueva tarea a la lista
      addTask(newTask) {
        this.tasks.push(newTask);
      },
  
      // Eliminar la tarea seleccionada
      deleteTask(task) {
        this.tasks = this.tasks.filter((t) => t.id !== task.id);
      },
    },
    created() {
      // Cargar las tareas desde la API cuando el componente es creado
      this.fetchTasks();
    },
  };
  </script>
  
  <style scoped>
  /* Puedes agregar estilos personalizados para esta vista combinada */
  button {
    margin-top: 10px;
    padding: 10px;
  }
  </style>
  