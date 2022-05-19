<template>
    <div>
        <HeaderComp 
            @getGenre="receiveGenre"
            @getAuthor="receiveAuthor"
            :GenreArr="genreArr"
            :AuthorArr="authorArr"
        />
        <main>
            <div v-if="this.isLoaded" class="disc-container">
                <CardComp
                    v-for="(album, index) in authorFilter"
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
            genreArr: [],
            authorArr: [],
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

                this.discArr.forEach(album => {
                    if(!this.genreArr.includes(album.genre)){
                        this.genreArr.push(album.genre);
                    }
                });

                this.discArr.forEach(album => {
                    if(!this.authorArr.includes(album.author)){
                        this.authorArr.push(album.author);
                    }
                });

            })
            .catch (err =>{
                console.log('ERROR', err)
            })
        },
        receiveGenre(genere){
            this.genreParam = genere;
            console.log('GENERE', genere);
        },
        receiveAuthor(author){
            this.authorParam = author;
            console.log('AUTORI', author)
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
                });

            }

            console.log(filteredAlbums);

            /* this.discArr.forEach((album) => {

                if(album.genre.toUpperCase().includes(this.genreParam.toUpperCase())){
                    
                    filteredAlbums.push(album);

                } else if (this.genreParam === 'default'){

                    filteredAlbums = this.discArr;

                }
            }) */
            
            return filteredAlbums;

        },

        authorFilter(){
            let authorFilteredAlbums = this.albumFilter;

            if(this.authorParam != 'default'){

                authorFilteredAlbums = this.albumFilter.filter(album => {
                    return album.author.toUpperCase().includes(this.authorParam.toUpperCase());
                });

            }
            return authorFilteredAlbums;
        }
    }

}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars';
@import '../assets/style/mixins';

main{
    min-height: 100vh;
    padding-top: 50px;
    background-color: $primary-color;
    .disc-container{
        @include dFlex;
        flex-wrap: wrap;
        width: 75%;
        margin: 0 auto;
    }
}
</style>