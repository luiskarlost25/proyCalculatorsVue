<template>
  <div id="app">
    <!-- Cabecera -->
    <Header />
    <div class="content">
      <div class="component-container">
      <Calculator>
      
      </Calculator>
    </div>
    <div class="component-container">
      <ConvertidorTemp>
        
      </ConvertidorTemp>
    </div>
    <div class="component-container">
      
      <ConvertidorMonedas>

      </ConvertidorMonedas>
      

    </div>
    </div>
   <div class="content">
    <Portafoliogalleria>
      
    </Portafoliogalleria>
   </div>
      <!-- Pie de Página -->
    <Footer />
   
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue';
import ConvertidorTemp from './components/ConvertidorTemp.vue';
import ConvertidorMonedas from './components/ConvertidorMonedas.vue';
import Portafoliogalleria from './components/Portafoliogalleria.vue';

import Header from './components/Header.vue';
import Footer from './components/Footer.vue';
export default {
  name: "App",
  components: {
    Header,
    Footer,
    Calculator,
    ConvertidorTemp,
    ConvertidorMonedas,
    Portafoliogalleria
  },
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  margin-top: 20px;


  display: flex;
  flex-direction:column;
  align-items: center; /* Centrar los componentes horizontalmente */
  width: 100%; /* Ocupa todo el ancho disponible */
  padding: 20px; /* Espaciado interno para el contenedor principal */
  box-sizing: border-box; /* Incluye el padding en el ancho */
}
#app3{
  display: grid;
  grid-template-rows: auto 1fr auto; /* Tres filas: Header, contenido, Footer */
  height: 100vh; /* Altura completa del viewport */
}

.content {
  display: flex; /* Alinea los tres componentes en fila */
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  gap: 20px; /* Espaciado entre componentes */
}
.component-container {
  width: 90%; /* Cada componente ocupa el 90% del ancho total */
  margin-bottom: 20px; /* Espacio entre componentes */
  display: flex;
  justify-content: center; /* Centra horizontalmente el contenido dentro del contenedor */
}
</style>
