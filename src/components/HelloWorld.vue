<template>
  <div class="hello">
    <h3>{{ temperstura }}</h3>
    <h5>{{ veter }}</h5>
    <h5>{{davlenie}}</h5>
    <button class="button" @click="onClick">Прогноз погоды</button>
  </div>
  <h3>{{ serverData }}</h3>
  <button @click="getServer">Ответ сервера</button>
</template>

<script>
import axios from "axios";

export default {
  name: 'HelloWorld',
  data(){
    return{
      temperstura: 23 + 'C',
      veter: 23 + 'км.ч',
      davlenie: 48 + '%',
      serverData: null
    }

  },
  methods: {
    onClick() {

    },
    getServer() {
      axios
          .get('https://www.foaas.com/cup/:Maxim')
          .then(response => (
              this.serverData = response.data
          ));
    },
  },
}
</script>


<style scoped>
.hello {
  margin: 0 auto;
}

.button {
  border-radius: 5px;
}
</style>
