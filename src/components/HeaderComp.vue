<template>
    <div class="header d-flex">
        <div class="spotify-logo">
            <a href="#">
                <img src="../assets/img/logo-small copia.svg" alt="spotify-logo">
            </a>
        </div>
        <div class="genre-select">
            <select name="genre" id="genre">
                <option selected>Choose a Genre</option>
                <option value="rock">Rock</option>
                <option value="pop">Pop</option>
                <option value="jazz">Jazz</option>
                <option value="metal">Metal</option>
            </select>

        </div>
    </div>
</template>

<script>

export default {
    name: 'HeaderComp'
}
</script>

<style lang="scss" scoped>
.header {
    height: 100px;
    padding: 0 25px;
    background-color: #2E3A46;
    justify-content: space-between;
    align-items: center;
    .spotify-logo{
        width: 80px;
        img{
            width: 80%;
            filter: invert(56%) sepia(99%) saturate(364%) hue-rotate(83deg) brightness(92%) contrast(83%);
        }
    }
    #genre{
        padding: 10px 25px;
        option{
            background-color: white;
        }
    }
}
</style>