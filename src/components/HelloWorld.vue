<template>
  <div class="hello">
    <button class="button" @click="onClick">Прогноз погоды</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data(){
    return{
      count: 23

    }

  },
  methods: {
    onClick() {

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
