<template>
    <div>
        <h1>Details Section Coming Soon!</h1>
        <div>
            <h2 style="text-align: center;">The Current Build Is:</h2>
            <p>Name: {{ buildName }}</p>
            <p>Profession: {{ buildProf }}</p>
            <h2 style="text-align: center;">The Currently Selected Skills are:</h2>
            <p>Heal: </p>
            <p>Utility 1: </p>
            <p>Utility 2: </p>
            <p>Utility 3: </p>
            <p>Elite: </p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'BuildDetails',
        props: {
            buildName: String,
            buildProf: String,
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