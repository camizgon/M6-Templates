<template>
  <div id="app">
    <div class="control-panel">
      <form>
        <div>
          <label for="backgroundColor">Color de fondo:</label>
          <input id="backgroundColor" type="text" v-model="figure.backgroundColor" />
        </div>
        <div>
          <label for="textColor">Color de texto:</label>
          <input id="textColor" type="text" v-model="figure.textColor" />
        </div>
        <div>
          <label for="showText">Mostrar texto:</label>
          <input id="showText" type="checkbox" v-model="figure.showText" />
        </div>
        <div>
          <label for="border">Borde:</label>
          <input id="border" type="range" min="0" max="10" v-model="figure.border" />
        </div>
        <div>
          <label for="content">Contenido textual:</label>
          <textarea id="content" v-model="figure.content"></textarea>
        </div>
        <div>
          <label for="fontFamily">Tipografía:</label>
          <select id="fontFamily" v-model="figure.fontFamily">
            <option value="Arial">Arial</option>
            <option value="Courier New">Courier New</option>
            <option value="Cursive">Cursive</option>
          </select>
        </div>
        <div>
          <label for="opacity">Opaco:</label>
          <input id="opacity" type="checkbox" v-model="figure.opaque" />
        </div>
        <div>
          <label>Tamaño de letra:</label>
          <input type="radio" id="small" value="small" v-model="figure.fontSize" />
          <label for="small">Pequeño</label>
          <input type="radio" id="medium" value="medium" v-model="figure.fontSize" />
          <label for="medium">Mediano</label>
          <input type="radio" id="large" value="large" v-model="figure.fontSize" />
          <label for="large">Grande</label>
        </div>
      </form>
    </div>

    <div class="figure" :style="figureStyles">
      <span v-if="figure.showText">{{ figure.content }}</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      figure: {
        backgroundColor: 'darkgreen',
        textColor: 'white',
        showText: true,
        border: 1,
        content: 'Awesome Vue.js',
        fontFamily: 'Arial',
        opaque: false,
        fontSize: 'medium',
      },
    };
  },
}
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
  border-radius: 10px;
  color: white;
  margin-right: 20px;
}

.control-panel form > div {
  margin-bottom: 15px;
}

.figure {
  background-color: green;
  width: 300px;
  height: 300px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  border-radius: 20px;
  text-align: center;
}
</style>
