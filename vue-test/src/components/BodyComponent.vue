<template>
    <div>
        <h1>Componente</h1>
        <h2>{{subtitle}}</h2>
        <button v-on:click="consoleLog">Click</button>
    </div>
</template>

<script>
export default {
  name: 'BodyComponent',
  data(){
      return {
          subtitle: "Subtitulo de mi componente"
      }
  },
  methods: {
      consoleLog: function(){
          console.log("Has clickado el botón")
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
