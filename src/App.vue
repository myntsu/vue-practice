<script>
export default {
  data() {
    return {
      fondo: "",
      colores: ["green", "purple", "pink", "black"],
      fuenteIndex: 0,
      pixeles: ["14px", "16px", "18px", "20px", "22px"],
      cuadroColor: "rgb(255,255,255)",
      tiempoElegido: '',
      periodoTiempo: 'Sin selección',
      colorFondoTiempo: '',
    };
  },

  computed: {
    fuente() {
      return this.pixeles[this.fuenteIndex];
    }
  },

  method: {
    actualizarTiempo() {
      if (this.tiempoElegido) {
        const [horas] = this.tiempoElegido.split(':').map(Number);

        if (horas >= 6 && horas < 12) {
          this.periodoTiempo = 'Mañana';
          this.colorFondoTiempo = 'beige';
        } else if (hours >= 12 && hours < 18) {
          this.periodoTiempo = 'Tarde';
          this.colorFondoTiempo = 'orange';
        } else {
          this.periodoTiempo = 'Noche';
          this.colorFondoTiempo = 'darkblue';
        }
      } else {
        this.periodoTiempo = 'Sin selección';
        this.colorFondoTiempo = '';
      }
    }
  }
};
</script>

<template>
  <div id="app">
    <div>
      <select v-model="fondo">
        <option value="">Elige un color</option>
        <option v-for="color in colores" :key="color">{{ color }}</option>
      </select>
      <h1 :style="{ background: fondo, 'font-size': fuente }" :class="{ 'text-white': fondo === 'black' }">Enlace de
        estilos
      </h1>
    </div>

    <div>
      <div><label for="pixeles">Elige un tamaño de pixeles</label></div>
      <input name="pixeles" id="pixeles" type="range" v-model="fuenteIndex" min="0" :max="pixeles.length - 1">
    </div>


    <div>
      <div><label for="colores">Elige un color</label></div>
      <input id="colores" type="color" v-model="cuadroColor">
      <div class="cuadro-color" :style="{ 'background-color': cuadroColor }">
      </div>
    </div>

    <div>
      <div><label for="tiempo">Elige una hora</label></div>
      <input type="time" name="tiempo" id="tiempo" v-model="tiempoElegido" @input="actualizarTiempo">
      <div class="tiempo">
        <span class="tiempo-texto" :style="{ 'background-color': colorFondoTiempo }">{{ periodoTiempo }}</span>
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

.tiempo {
  background-color: white;
  width: 100px;
  height: 100px;
}
</style>