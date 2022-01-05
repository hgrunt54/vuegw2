<template>
    <div class="Profession">
        <h1 class="h1">Create a Guild Wars 2 Build</h1>
        <label for="name">Name: </label>
        <input id="name" v-model="name" v-on:change="nameChange"/>
        <label for="sel_prof"> Profession: </label>
        <select id="sel_prof" v-model='prof' v-on:change="profChange">
            <option disabled value>Please Select One</option>
            <option value="Mesmer">Mesmer</option>
            <option value="Necromancer">Necromancer</option>
        </select>
    </div>
</template>

<script>
    export default {
        name: 'Profession',
        data: function() {
            return {
                name: '',
                prof: '',
            }
        },
        methods: {
            nameChange() {
                this.$emit('nameUpdate', this.name)
            },
            profChange() {
                this.$emit('profUpdate', this.prof)
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
</style>
