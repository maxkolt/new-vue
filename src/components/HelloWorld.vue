<template>
  <div class="hello">
    <h3>{{ temperstura }}</h3>
    <h5>{{ veter }}</h5>
    <h5>{{davlenie}}</h5>
    <button class="button" @click="onClick">Прогноз погоды</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data(){
    return{
      temperstura: 23 + 'C',
      veter: 23 + 'км.ч',
      davlenie: 48 + '%'

    }

  },
  methods: {
    onClick() {
      this.;
    }
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
