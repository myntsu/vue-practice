<script>
export default {
  data() {
    return {
      fondo: "",
      colores: ["green", "purple", "pink", "black"],
      fuenteIndex: 0,
      pixeles: ["14px", "16px", "18px", "20px", "22px"],
      cuadroColor: "rgb(255,255,255)",
    };
  },

  computed: {
    fuente() {
      return this.pixeles[this.fuenteIndex];
    }
  }
}
</script>

<template>
<div id="app">
  <div>
    <select v-model="fondo">
      <option value="">Elige un color</option>
      <option v-for="color in colores" :key="color">{{ color }}</option>
    </select>
    <h1 :style="{background: fondo, 'font-size': fuente}" :class="{'text-white': fondo === 'black'}">Enlace de estilos</h1>
  </div>

  <div>
    <div><label for="pixeles">Elige un tamaño de pixeles</label></div>
    <input name="pixeles" id="pixeles" type="range" v-model="fuenteIndex" min="0" :max="pixeles.length - 1">
  </div>


  <div>
    <div><label for="colores">Elige un color</label></div>
    <input id="colores" type="color" v-model="cuadroColor" >
    <div class="cuadro-color" :style="{'background-color': cuadroColor}">
  </div>

  </div>
</div> 
</template>

<style scoped>
#app {
  display: grid;
  gap: 3rem;
}

.text-white {
  color: white;
}

.cuadro-color {
  width: 200px;
  height: 200px;
}
</style>