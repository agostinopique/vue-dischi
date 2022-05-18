<template>
    <div>
        <HeaderComp />
        <main>
            <div v-if="isLoaded" class="disc-container">
                <CardComp
                    v-for="(album, index) in SpotifyAlbum"
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
    props: {
        SpotifyAlbum: Array,
        isLoaded: Boolean
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