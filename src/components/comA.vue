<template>
  <div>
    <h1>
      小计：{{total}}
      总价：{{$store.getters.totalPrice}}
    </h1>
    <h2>
      {{msg}}
    </h2>
  </div>
</template>

<script>
  // import bus from '../bus'
  export default {
    data (){
      return {
        msg: ''
      }
    },
    created(){
    //   bus.$on('toData', (msg) => {
    //     this.msg = msg
    // })
      this.$bus.$on('toData', (msg) => {
        this.msg = msg
    })
    },
    // props:{
    //   count: {
    //     type: Number
    //   },
    //   price: {
    //     type: Number
    //   }
    // },
    computed: {
      total (){
        return this.$store.state.count * this.$store.state.price
      }
    },
    name: "com-a"
  }
</script>

<style scoped>

</style>
