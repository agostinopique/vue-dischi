<template>
    <div>
        <HeaderComp 
            @getGenre="receiveGenre"
            @getAuthor="receiveAuthor"
            :AlbumArr="discArr"
        />
        <main>
            <div v-if="this.isLoaded" class="disc-container">
                <CardComp
                    v-for="(album, index) in albumFilter"
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
            genreParam: '',
            authorParam: ''
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
        receiveGenre(genere){
            this.genreParam = genere;
        },
        receiveAuthor(author){
            this.authorParam = author;
        }
    },


    computed: {
        albumFilter(){
            let filteredAlbums = [];

            // ALTERNATIVA CON FILTER
            if(this.genreParam === 'default'){

                filteredAlbums = this.discArr;

            } else {

                filteredAlbums = this.discArr.filter(album => {
                    return album.genre.toUpperCase().includes(this.genreParam.toUpperCase());
                })

            }

            /* this.discArr.forEach((album) => {

                if(album.genre.toUpperCase().includes(this.genreParam.toUpperCase())){
                    
                    filteredAlbums.push(album);

                } else if (this.genreParam === 'default'){

                    filteredAlbums = this.discArr;

                }
            }) */
            
            return filteredAlbums;

        }
    }

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