<template>
    <div class="genre-select">

        <select
            v-model="value"
            @change="$emit('genreChange', value)"
            name="genre" id="genre">
            
            <option value="default" selected>Choose a Genre</option>
            <option value="rock">Rock</option>
            <option value="pop">Pop</option>
            <option value="jazz">Jazz</option>
            <option value="metal">Metal</option>
        </select>
    
    </div>
</template>

<script>
export default {
    name: 'SelectComp',

    data(){
        return {
            value: 'default'
        }
    }
}
</script>

<style lang="scss" scoped>
#genre{
        padding: 10px 25px;
        option{
            background-color: white;
        }
    }
</style>