<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometro :tempoEmSegundos="tempoEmSegundos" />
    <button class="button" @click="iniciar" :disabled="cronometroRodando">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span> play</span>
    </button>
    <button class="button" @click="finalizar" :disabled="!cronometroRodando">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cronometro from "./Cronometro.vue";

export default defineComponent({
  name: "Temporizador-time",
  components: {
    Cronometro
  },
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      cronometroRodando: false
    };
  },

  methods: {
    iniciar() {
      //começar a contar
      // atribuir 1 segundo = 1000 ms
      this.cronometroRodando = true
      this.cronometro = setInterval(() => {
        //console.log('incrementando o contador de segundos')
        this.tempoEmSegundos += 1;
      }, 1000);

      //console.log('iniciando');
    },
    finalizar() {
      // console.log('finalizando');
      this.cronometroRodando = false
      clearInterval(this.cronometro);
    },
  },
});
</script>