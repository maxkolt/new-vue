<template>
  <div id="app">
    <h1 class="block">{{ firstName }}</h1>
    <img class="face" alt="foto" src="./assets/face.png"/>
    <a v-bind:href="linkUrl">My GitHub</a>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <h3>{{ count }}</h3>
    <h3>Ответ от сервака: {{ serverData }}</h3>

    <button @click="clickCounter"><b>sdfdsf</b></button>
    <button @click="getFromServer">From server</button>
    <button @click="getFromServer">From server2</button>
    <footer class="connect">

    </footer>
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
      firstName: 'Maxim Koltovich',
      count: 0,
      serverData: null,
      serverData2: null,
      linkUrl: "https://github.com/maxkolt"
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
    getFromDataServer() {
      axios
          .get('https://www.foaas.com/cup/:Maxim')
          .then(response => (
              this.serverData = response.data.bpi.USD.code
          ));
    }

  }
}
</script>

<style scoped>
.block {
  margin: 0 auto;
  text-align: center;
  padding: 50px;
  border-radius: 10px;
  background-color: seagreen;
}

.face {
  width: 100px;
  height: 100px;
}

</style>
