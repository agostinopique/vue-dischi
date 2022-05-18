<template>
  <div>
    <MainComp 
      :SpotifyAlbum="discArr"
      :isLoaded="isLoaded"
    />
  </div>
</template>

<script>
import axios from 'axios';
import MainComp from './components/MainComp.vue'

export default {
  name: 'App',
  components: { 
    MainComp
  },
  data(){
    return{
      apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
      discArr: [],
      isLoaded: false
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
          this.isLoaded = true;
      })
    }
  }
}
</script>

<style lang="scss">
  @import './assets/style/general';
</style>
