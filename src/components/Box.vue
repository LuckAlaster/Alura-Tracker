<template>
  <div class="box formulario has-text-weight-bold" :style="estiloBox">
    <slot></slot>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Box-template",
  data (){
    return{
      estiloBox: { 
      backgroundColor: '#faf0ca'
      }
    }
  }
});
</script>