<template>
    <div>
        <HeaderComp 
            @genreChange="searchGenre" 
        />
        <main>
            <div v-if="this.isLoaded" class="disc-container">
                <CardComp
                    v-for="(album, index) in searchGenre"
                    :key="`album-${index}`"
                    :AlbumCard="album"
                />
            </div>

            <div v-else>
                <LoaderComp />
            </div>
        </main>
    </div>
</template>

<script>
import axios from 'axios';
import CardComp from './CardComp.vue';
import HeaderComp from './HeaderComp.vue';
import LoaderComp from './LoaderComp.vue';


export default {
    name: "MainComp",
    components: {
    CardComp,
    HeaderComp,
    LoaderComp
    },

    data(){
        return{
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            discArr: [],
            isLoaded: false,
            searchParam: ''
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
        },
       /*  searchGenre(string){
            this.searchParam = string;
            
        } */
    },

/*
    computed: {
        searchGenre(){
           

           return this.discArr;
        }
    }*/

}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars';

main{
    min-height: 100vh;
    padding-top: 50px;
    background-color: $primary-color;
    .disc-container{
        display: flex;
        flex-wrap: wrap;
        width: 75%;
        margin: 0 auto;
    }
}
</style>