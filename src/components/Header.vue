<template>
    <header class="header">
      <h1>Mi Aplicación</h1>
      <nav>
        <a href="#">Inicio</a>
        <a href="#">Sobre Nosotros</a>
        <a href="#">Contacto</a>
      </nav>
    </header>
  </template>
  
  <script>
  export default {
    name: "Header",
  };
  </script>
  
  <style scoped>
  .header {
    background-color: #056889;
    color: white;
    padding: 1rem;
    text-align: center;
  }
  .header nav a {
    margin: 0 1rem;
    color: white;
    text-decoration: none;
  }
  .header nav a:hover {
    text-decoration: underline;
  }
  </style>
  