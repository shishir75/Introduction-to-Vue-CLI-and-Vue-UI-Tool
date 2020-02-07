<template>
  <div id="app">
    <tasks/>

    <div :class="classObject">{{ value }}</div>
    <div :style="{ fontSize: ( value*10 ) + 'px' }">{{ value }}</div>

    <button type="button" @click="value++">+</button>
    <button type="button" @click="value--">-</button>
    <button type="button" @click="error = !error">Error</button>
    <button type="button" @click="warning = !warning">Warning</button>

  </div>
</template>

<script>
  import Tasks from "./components/Tasks";

  export default {
    name: 'app',
    components: {
      Tasks
    },
    data: function () {
      return {
        value: 1,
        error: false,
        warning: false,
      }
    },

    computed: {
      classObject: function () {
        return {
          'red-error' : this.value > 5,
          'green-error' : this.value <= 5,
          'yellow-warning' : this.warning
        }
      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  .red-error {
    background-color: darkred;
  }

  .green-error {
    background-color: darkgreen;
  }
  .yellow-warning {
    text-decoration: underline;
  }
</style>
