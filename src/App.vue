<template>
  <article>
    
  <form class="contenedor-form">
    <label for="colorFondo">Color de Fondo</label> <br>
    <input type="text" v-model="colorFondo" id="colorFondo"> <br>

    <label for="colorTexto">Color de Texto</label> <br>
    <input type="text" v-model="colorTexto" id="colorTexto"> <br>

    <label for="mostrarTexto">Mostrar Texto</label>
    <input type="checkbox" id="mostrarTexto" v-model="mostrarTexto"> <br>

    <label for="borde">Borde</label> <br>
    <input type="range" id="borde" v-model="borde"> <br>

    <label for="texto">Contenido Textual</label> <br>
    <textarea id="texto" cols="30" rows="10" placeholder="Sample Text" v-model="contenidoTextual"></textarea> <br>

    <label for="tipografia">Tipografía</label> <br>
    <select id="tipografia" v-model="tipografia">
      <option v-for="tipo in opcionesTipografia" :key="tipo" :value="tipo[0]" :label="tipo[1]">
        {{ tipo[0] }}
      </option>
    </select> <br>

    <label for="opaco">Opaco</label>
    <input type="checkbox" id="opaco" v-model="opaco"> <br>

    <label>Tamaño de Letra</label> <br>
    <div v-for="porte in opcionesTamano" :key="porte" class="inline">
      <input type="radio" name="porteLetra" :id="porte[1]" v-model="tamanoLetra" :value="porte[0]">
      <label :for="porte[1]">{{ porte[1] }}</label>
    </div>

  </form>

  <div class="contenedor-figura">
      <div class="figura"
      :style="{ 
        'background-color': colorFondo,
        'color': colorTexto,
        'border-radius': borde + 'px',
        'font-style': tipografia,
        'font-size': tamanoLetra,
      }"
      :class="{
        translucido: !opaco,
      }">
        <p v-show="mostrarTexto">
          {{ contenidoTextual }}
        </p>
      </div>
  </div>

  </article>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      colorFondo: "green",
      colorTexto: "#ffffff",
      mostrarTexto: true,
      borde: 10,
      contenidoTextual: "Sample Text",
      opcionesTipografia: [["normal", "Normal"], ["italic", "Cursiva"]],
      tipografia: "normal",
      opaco: true,
      opcionesTamano: [["x-small", "Pequeño"], ["medium", "Mediano"], ["xx-large", "Grande"]],
      tamanoLetra: "medium",
    }
  },

}
</script>

<style scoped>
  .figura{
    height: 200px;
    width: 200px;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    margin: 50px;
    /* font-family: Georgia, 'Times New Roman', Times, serif; */
  }

  .translucido{
    opacity: 0.1;
  }

  article{
    display: flex; 
    align-items: center;
  }

  .contenedor-form{
    width: 40%;
    background-color: rgb(37, 1, 1); 
    color: rgb(255, 255, 255); 
    margin: 1%;
    padding: 2%;
    border-radius: 5px;
  } 

  .contenedor-figura{
    display: flex;
    align-items: center;
    justify-content: center;
    width: 40%;
    margin: 1%;
  }

  .inline{
    display: inline;
  }
</style>
