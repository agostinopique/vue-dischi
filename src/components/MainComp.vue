<template>
    <main>
        <div class="disc-container">
            <CardComp
                v-for="(album, index) in SpotifyAlbum"
                :key="`album-${index}`"
                :AlbumCard="album"
            />
        </div>
    </main>
</template>

<script>
import CardComp from './CardComp.vue';


export default {
    name: "MainComp",
    components: {
        CardComp
    },
    props: {
        SpotifyAlbum: Array
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