<template>
    <div class="app-container">
      <!-- Header que se muestra en todas las vistas -->
      <header class="app-header">
        <nav>
          <ul class="nav-list">
            <li><NuxtLink to="/">Inicio</NuxtLink></li>
            <li><NuxtLink to="/automoviles">Automóviles</NuxtLink></li>
            <li><NuxtLink to="/disenadores">Diseñadores</NuxtLink></li>
            <li><NuxtLink to="/fabricantes">Fabricantes</NuxtLink></li>
          </ul>
        </nav>
      </header>
  
      <main class="app-main">
        <NuxtPage />
      </main>
  
      <footer class="app-footer">
        <p>&copy; 2024 CarCatalogo. Todos los derechos reservados.</p>
      </footer>
    </div>
  </template>
  
  <script setup>
  
  </script>
  
  <style scoped>
  /* Estilos generales */
  .app-container {
    display: flex;
    flex-direction: column;
    height: 100vh;
    background: linear-gradient(135deg, #ff6f61, #ff9a8b); 
  }
  
  /* Header */
  .app-header {
    background-color: #2c3e50; 
    color: #fff;
    padding: 20px;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 1000; 
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2); 
  }
  
  .nav-list {
    list-style-type: none;
    padding: 0;
    display: flex;
    justify-content: center;
  }
  
  .nav-list li {
    margin: 0 15px;
  }
  
  .nav-list a {
    color: white;
    text-decoration: none;
    font-size: 1.2em;
    padding: 10px 15px;
    border-radius: 5px;
    transition: background-color 0.3s;
  }
  
  .nav-list a:hover {
    background-color: #f39c12;
    text-decoration: none;
  }
  
  /* Contenido principal */
  .app-main {
    flex: 1;
    padding: 40px;
    background-color: #f8f9fa;
    color: #333;
    font-size: 1.2em;
    overflow-y: auto;
    margin-top: 80px; 
  }
  
  /* Footer */
  .app-footer {
    background-color: #2c3e50; 
    color: #fff;
    text-align: center;
    padding: 20px;
    position: fixed;
    bottom: 0;
    width: 100%;
    box-shadow: 0 -4px 10px rgba(0, 0, 0, 0.2); 
  }
  
  .app-footer p {
    margin: 0;
    font-size: 1em;
  }
  
  a {
    text-decoration: none;
    color: inherit;
  }
  
  a:hover {
    text-decoration: underline;
  }
  </style>
  