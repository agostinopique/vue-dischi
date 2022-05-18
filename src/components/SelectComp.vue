<template>
    <div class="select-container">
        
        <div class="genre-select">
    
            <select
                v-model="valueGenre"
                @change="$emit('genreChange', valueGenre)"
                name="genre" id="genre">
                
                <option value="default" selected>Choose a Genre</option>
                <option 
                    v-for="(genre, index) in genreFilter"
                    :key="`album-${index}`"
                    :value="genre">{{genre}}</option>
            </select>
    
        </div>
        <div class="genre-select">
    
            <select
                v-model="valueAuthor"
                @change="$emit('authorChange', valueAuthor)"
                name="genre" id="author">
                
                <option value="default" selected>Choose an Author</option>
                <option 
                    v-for="(author, index) in authorFilter"
                    :key="`album-${index}`"
                    :value="author">{{author}}</option>
            </select>
    
        </div>
    </div>
</template>

<script>
export default {
    name: 'SelectComp',

    props: {
        AlbumArr: Array
    },

    data(){
        return {
            valueGenre: 'default',
            valueAuthor: 'default'
        }
    },

    computed: {
        genreFilter(){
            let genreArr = [];

            this.AlbumArr.forEach(album => {
                if(!genreArr.includes(album.genre)){
                    genreArr.push(album.genre);
                }
            })
            return genreArr;
        },

        authorFilter(){
            let authorArr = [];

            this.AlbumArr.forEach(album => {
                if(!authorArr.includes(album.author)){
                    authorArr.push(album.author);
                }
            });
            return authorArr
        }

    }
}
</script>

<style lang="scss" scoped>
.select-container{
    display: flex;
}
#genre,
#author{
    padding: 10px 25px;
    option{
        background-color: white;
    }
}

#author{
    margin-left: 5px;
}
</style>