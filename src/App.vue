<template>
  <div id="app">
    <!-- Barra de navegación con Bootstrap -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
      <div class="container-fluid">
        <router-link class="navbar-brand" to="/">Gestión de Tareas</router-link>
        <button 
          class="navbar-toggler" 
          type="button" 
          data-bs-toggle="collapse" 
          data-bs-target="#navbarNav"
          aria-controls="navbarNav" 
          aria-expanded="false" 
          aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <router-link class="nav-link" to="/">Home</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/addtask">Agregar Tarea</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/tasklist">Lista de Tareas</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/combinedview">Lista Combinada</router-link>
            </li>
          </ul>
        </div>
      </div>
    </nav>

    <!-- Aquí se cargará el componente correspondiente a la ruta seleccionada -->
    <div class="container mt-4">
      <router-view />
    </div>
  </div>
</template>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.navbar-brand {
  font-weight: bold;
}

.nav-link {
  font-weight: 500;
}

.nav-link.router-link-exact-active {
  color: #ffdd57 !important;
}
</style>
