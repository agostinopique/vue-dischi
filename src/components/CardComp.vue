<template>
    <div class="card-container">
        <div class="disc-img">
            <img :src="AlbumCard.poster" :alt="AlbumCard.title">
        </div>
        <div class="disc-text">
            <h4>{{AlbumCard.title}}</h4>
            <span class="album-title">{{AlbumCard.author}}</span>
            <span>{{AlbumCard.year}}</span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CardComp',
    props:{
        AlbumCard: Object
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars';

.card-container{
    width: calc((100% - 100px) / 5);
    min-width: 180px; 
    min-height: 300px;
    margin: 10px;
    padding: 15px;
    background-color: $secondary-color;
    text-align: center;
    .disc-text{
        display: flex;
        flex-direction: column;
        padding-top: 10px;
        h4{
            color: white;
            text-transform: uppercase;
        }
        span{
            color: #7C7977
        }
        .album-title{
            font-size: 22px;
        }
    }
}
.disc-img img{
    width:100%;
}
</style>