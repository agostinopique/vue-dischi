<template>
    <div class="header">
        <div class="header-container">

            <div class="spotify-logo">
                <a href="#">
                    <img src="../assets/img/logo-small copia.svg" alt="spotify-logo">
                </a>
            </div>

            <SelectComp 
                @genreChange="searchGenre"
            />
        </div>
    </div>
</template>

<script>
import SelectComp from './SelectComp.vue'

export default {
    name: 'HeaderComp',
    components: {
        SelectComp
    },

    data(){
        return{
            searchParam: ''
        }
    },

    methods: {
        searchGenre(genere){
            this.searchParam = genere;
            this.$emit('getGenre', genere);
            console.log('GENERE',this.searchParam);
        }
    }
    
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars';

.header {
    height: 100px;
    padding: 0 25px;
    background-color: $secondary-color;
    .header-container{
        display: flex;
        height: 100%;
        width: 75%;
        margin: 0 auto;
        justify-content: space-between;
        align-items: center;
    }
    .spotify-logo{
        width: 80px;
        img{
            width: 80%;
            filter: invert(56%) sepia(99%) saturate(364%) hue-rotate(83deg) brightness(92%) contrast(83%);
        }
    }
    
}
</style>