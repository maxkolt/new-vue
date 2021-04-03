<template>
  <div id="app">
    <h1 class="block">{{ firstName }}</h1>
    <img class="face" alt="foto" src="./assets/face.png"/>
    <a :href="linkUrl">My GitHub</a>
    <h5>
      <img alt="country" src="./assets/iconsCountry.png">
      Russia, Moscow
    </h5>
    <h5>
      <img alt="year" src="./assets/iconsYear.png">
      12 / 08 / 1991
    </h5>
    <h5 class="mail">
      <img alt="icons" src="./assets/iconsMail.png">
      {{ gmail }}
    </h5>


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
      gmail: '12345kolt@gmail.com',
      linkUrl: "https://github.com/maxkolt",
      count: 0,
      serverData: null,
      serverData2: null,
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
* {
  margin: 0;

}

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

.mail {
  color: cadetblue;
}

</style>
