<template>
    <h1 class="h1">Find a Guild Wars 2 Build</h1>
    <label for="sel_prof"> Profession: </label>
    <select id="sel_prof" v-model='prof' v-on:change="profChange">
        <option value="All">All Builds</option>
        <option value="Mesmer">Mesmer</option>
        <option value="Necromancer">Necromancer</option>
    </select>
    <p></p>
    <table>
        <th>Name </th>
        <th>Profession </th>
        <th>Heal </th>
        <th>Utility 1 </th>
        <th>Utility 2 </th>
        <th>Utility 3 </th>
        <th>Elite </th>
    </table>
</template>

<script>
    export default {
        name: 'Find',
        data() {
            return {

            }
        }
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
    table {
        margin-left: auto;
        margin-right: auto;
    }
</style>