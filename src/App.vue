<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">

    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <h3>{{ count }}</h3>
    <h3>Ответ от сервака: {{ serverData }}</h3>

    <button @click="clickCounter"><b>sdfdsf</b></button>
    <button @click="getFromServer">From server</button>
    <button @click="getFromServer">From server2</button>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios'

export default {

  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      count: 0,
      serverData: null,
      serverData2: null
    }
  },
  methods: {
    clickCounter() {
      this.count = this.count + 1;
    },
    getFromServer() {
      axios
          .get('https://api.coindesk.com/v1/bpi/currentprice.json')
          .then(response => (
              this.serverData = response.data.bpi.USD.code
          ));
    },
  getFromDataServer(){
      axios
          .get('https://www.foaas.com/cup/:Maxim')
          .then(response => (
              this.serverData = response.data.bpi.USD.code
          ));
  }

  }
}
</script>

<style>

</style>
