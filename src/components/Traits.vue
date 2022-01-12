<template>
    <div>
        <h1>Traits Section Coming Soon!</h1>
        <Traitline />
        <Traitline />
        <Traitline />
    </div>
</template>

<script>
    import Traitline from './Traitline.vue'

    export default {
        name: 'Traits',
        components: {
            Traitline
        },
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h1 {
        background: lightgray;
    }

    h3 {
        margin: 40px 0 0;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }
</style>