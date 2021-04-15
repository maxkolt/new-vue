<template>
  <div class="hello">

    <div>
      <b-card
          title="Card Title"
          img-src=""
          img-alt="Image"
          img-top
          tag="article"
          style="max-width: 20rem;"
          class="mb-2"
      >
        <b-card-text>
         <h3>{{ temperatura }}</h3>
        </b-card-text>
        <b-button @click="weatherResponse" href="#" variant="primary">Узнать погоду</b-button>
      </b-card>
    </div>
  </div>
</template>

<script>

import axios from "axios";

export default {
  name: 'HelloWorld',
  data() {
    return {
      temperatura: '',
      access_key: 'a54d1451af691342e975fde0186820bf',
      serverData: null
    }

  },
  created() {
    const cuurent = this.$axios('https://api.weatherstack.com/current' + `  ? ${this.access_key} = YOUR_ACCESS_KEY ` + '& query = New York')
          .then(response => r.data.request.type.location.name)



          this.temperatura = request.type
    },

  methods: {


  }
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
