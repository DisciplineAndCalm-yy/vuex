<template>
  <div style="border:1px solid #000; display: flex;">
    <comA :price="price" :count="count"></comA>
    <comB :count="count" @add="add" @reduce="reduce"></comB>
    <h2>单价：{{price}}</h2>
    <input type="text" v-model="count">
    <button @click="CHANGE_COUNT(count)">改变</button>
    <br>
    <button @click="handleAsync">异步操作</button>
  </div>
</template>

<script>
  import comA from './comA';
  import comB from './comB';
  import { mapMutations } from 'vuex';
  export default {
    name: "home",
    data (){
      return {
        count: 0,
        price: 19.8
      }
    },
    components: {
      comA,
      comB
    },
    methods: {
      add (){
        this.count++
      },
      reduce (){
        this.count--
      },
      changeCount (){
        this.$store.commit('CHANGE_COUNT', this.count)
      },
      ...mapMutations(['CHANGE_COUNT']),
    handleAsync (){
      // setTimeout(() => {
      //   this.CHANGE_COUNT(this.count)
      // }, 3000)
      this.$store.dispatch('handleAsyncAction', 12)
    }
  }
  }
</script>

<style scoped>

</style>
