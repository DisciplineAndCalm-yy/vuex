<template>
  <div>
    <count></count>
    <input type="text" v-model="count">
    <button @click="changeCount">改变</button>
  </div>
</template>

<script>
  import count from './count'

  export default {
    name: "vuex-demo",
    components: {
      count
    },
    methods: {
      changeCount (){
        this.$store.commit('CHANGE_COUNT', this.count)
      }
    }
  }
</script>

<style scoped>

</style>
