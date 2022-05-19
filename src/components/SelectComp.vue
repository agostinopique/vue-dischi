<template>
    <div class="select-container">
        
        <div class="genre-select">
    
            <select
                v-model="valueGenre"
                @change="$emit('genreChange', valueGenre)"
                name="genre" id="genre">
                
                <option value="default" selected>Choose a Genre</option>
                <option 
                    v-for="(genre, index) in GenreArr"
                    :key="`genre-${index}`"
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
                    v-for="(author, index) in AuthorArr"
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
        GenreArr: Array,
        AuthorArr: Array
    },

    data(){
        return {
            valueGenre: 'default',
            valueAuthor: 'default'
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/mixins';
.select-container{
    @include dFlex;
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