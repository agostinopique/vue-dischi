<template>
  <div>
    <HeaderComp />
    <MainComp :SpotifyAlbum="discArr"/>
  </div>
</template>

<script>
import axios from 'axios';
import MainComp from './components/MainComp.vue'
import HeaderComp from './components/HeaderComp.vue'

export default {
  name: 'App',
  components: { 
    MainComp, 
    HeaderComp 
  },
  data(){
    return{
      apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
      discArr: []
    }
  },
  mounted(){
    this.getAPI()
  },
  methods: {
    getAPI(){
      axios.get(this.apiUrl)
        .then((res)=> {
          this.discArr = res.data.response;
          console.log(res.data.response);
      })
    }
  }
}
</script>

<style lang="scss">
  @import './assets/style/general';
</style>
