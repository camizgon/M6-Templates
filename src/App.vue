<template>
  <div id="app">
    <div class="control-panel">
      <form @submit.prevent>
        <div>
          <label for="backgroundColor">Color de fondo:</label>
          <input id="backgroundColor" type="text" v-model="colorDeFondo" />
        </div>
        <div>
          <label for="textColor">Color de texto:</label>
          <input id="textColor" type="text" v-model="colorDeTexto" />
        </div>
        <div>
          <label for="showText">Mostrar texto:</label>
          <input id="showText" type="checkbox" v-model="mostrarTexto" />
        </div>
        <div>
          <label for="border">Grosor del borde:</label>
          <input id="border" type="range" min="0" max="10" v-model="grosorDeBorde" />
        </div>
        <div>
          <label>Contenido textual:</label>
          <input type="radio" id="content1" value="Texto mostrado" v-model="opinion" />
          <label for="content1">Mostrar texto</label>
        </div>
        <div>
          <label for="fontFamily">Tipografía:</label>
          <select id="fontFamily" v-model="tipografia">
            <option v-for="font in fonts" :key="font" :value="font">{{ font }}</option>
          </select>
        </div>
        <div>
          <label for="opacity">Opaco:</label>
          <input id="opacity" type="checkbox" v-model="opaco" />
        </div>
        <div>
          <label>Tamaño de letra:</label>
          <input type="radio" id="small" value="pequeño" v-model="radio" />
          <label for="small">Pequeño</label>
          <input type="radio" id="medium" value="mediano" v-model="radio" />
          <label for="medium">Mediano</label>
          <input type="radio" id="large" value="grande" v-model="radio" />
          <label for="large">Grande</label>
        </div>
      </form>
    </div>

    <div v-show="mostrarTexto" class="container"
      :style="{
        backgroundColor: colorDeFondo,
        color: colorDeTexto,
        borderWidth: grosorDeBorde + 'px',
        opacity: opaco ? 0.5 : 1,
        fontFamily: selectedFont
      }"
      :class="[fontSizeClass]">
      <div>
        <p v-if="mostrarTexto">Su opinión: {{ opinion }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      colorDeFondo: '',
      colorDeTexto: '',
      mostrarTexto: true,
      grosorDeBorde: 1,
      opinion: '',
      tipografia: '',
      opaco: false,
      radio: '', // Propiedad para los radios de tamaño de letra
      fonts: ["Arial", "Courier New", "Cursive"],
    };
  },
  computed: {
    fontSizeClass() {
      switch (this.radio) {
        case 'pequeño':
          return 'pequeño';
        case 'mediano':
          return 'mediano';
        case 'grande':
          return 'grande';
        default:
          return '';
      }
    },
    selectedFont() {
      return this.tipografia || 'Arial';
    }
  }
};
</script>

<style>
#app {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background-color: #1f2021;
}

.control-panel {
  background-color: #324a5e;
  padding: 20px;
  border-radius: 20px;
  color: white;
  margin-right: 20px;
}

.control-panel form > div {
  margin-bottom: 15px;
}

.container {
  font-weight: bold;
  width: 200px;
  height: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.pequeño {
  font-size: small;
}

.mediano {
  font-size: medium;
}

.grande {
  font-size: xx-large;
}
</style>

