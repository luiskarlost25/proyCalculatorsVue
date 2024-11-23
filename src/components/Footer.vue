<template>
    <footer class="footer">
      <p>© 2024 Mi Aplicación. Todos los derechos reservados.</p>
      <div class="social-links">
        <a href="#" target="_blank">Facebook</a>
        <a href="#" target="_blank">Twitter</a>
        <a href="#" target="_blank">Instagram</a>
      </div>
    </footer>
  </template>
  
  <script>
  export default {
    name: "Footer",
  };
  </script>
  
  <style scoped>
  .footer {
    background-color: #333;
    color: white;
    padding: 1rem;
    text-align: center;
  }
  .footer .social-links a {
    margin: 0 1rem;
    color: #4caf50;
    text-decoration: none;
  }
  .footer .social-links a:hover {
    text-decoration: underline;
  }
  </style>
  