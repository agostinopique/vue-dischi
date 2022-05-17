<template>
  <div>
    <HeaderComp />
    <MainComp />
  </div>
</template>

<script>
// import axios from 'axios';
import MainComp from './components/MainComp'
import HeaderComp from './components/HeaderComp'

export default {
  name: 'App',
  components: { 
    MainComp, 
    HeaderComp 
  },
/*   mounted(){
    this.getApi()
  },
  methods: {
    getApi(){
      axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    }
  } */
}
</script>

<style lang="scss">
  @import './assets/style/general';
</style>
