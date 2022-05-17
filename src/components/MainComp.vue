<template>
    <div>
        <CardComp />
    </div>
</template>

<script>
import CardComp from './CardComp.vue'


export default {
    name: "MainComp",
    component: {
        CardComp
    }
}
</script>

<style lang="scss" scoped>
div{
    min-height: 100vh;
    background-color: #1E2D3B;
}
</style>