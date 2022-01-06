<template>
    <h1 class="h1">Find a Guild Wars 2 Build</h1>
    <label for="sel_prof"> Profession: </label>
    <select id="sel_prof" v-model='prof' v-on:change="profChange">
        <option value="All">All Builds</option>
        <option value="Mesmer">Mesmer</option>
        <option value="Necromancer">Necromancer</option>
    </select>
    <button @click="showResults"> Search </button>
    <p></p>
    <table id="tblResults" class="results">
        <th>Name </th>
        <th>Profession </th>
        <th>Heal </th>
        <th>Utility 1 </th>
        <th>Utility 2 </th>
        <th>Utility 3 </th>
        <th>Elite </th>
        <tr>
            <td class="seps">{{ Name }}</td>
            <td class="seps">{{ Prof }}</td>
            <td>
                <img :src="imgHeal" />
                <p>{{ Heal }}</p>
            </td>
            <td>
                <img :src="imgUtility1" />
                <p>{{ Utility1 }}</p>
            </td>
            <td>
                <img :src="imgUtility2" />
                <p>{{ Utility2 }}</p>
            </td>
            <td>
                <img :src="imgUtility3" />
                <p>{{ Utility3 }}</p>
            </td>
            <td>
                <img :src="imgElite" />
                <p>{{ Elite }}</p>
            </td>
        </tr>
    </table>
</template>

<script>
    export default {
        name: 'Find',
        data() {
            return {
                build: {},
                Name: '',
                Prof: '',
                Heal: '',
                Utility1: '',
                Utility2: '',
                Utility3: '',
                Elite: '',

                imgHeal: require('@/assets/images/skills/default/default_skill.png'),
                imgUtility1: require('@/assets/images/skills/default/default_skill.png'),
                imgUtility2: require('@/assets/images/skills/default/default_skill.png'),
                imgUtility3: require('@/assets/images/skills/default/default_skill.png'),
                imgElite: require('@/assets/images/skills/default/default_skill.png'),
            }
        },
        created: async function () {
            const routes = await fetch("http://localhost:5000/buildQuery");
            const gObject = await routes.json();
            this.build = gObject;
        },
        methods: {
            showResults() {
                this.Name = this.build.bName;
                this.Prof = this.build.bProf;
                this.Heal = this.build.bHeal;
                this.Utility1 = this.build.bUtility1;
                this.Utility2 = this.build.bUtility2;
                this.Utility3 = this.build.bUtility3;
                this.Elite = this.build.bElite;

                this.imgHeal = this.build.bimgHeal
                this.imgUtility1 = this.build.bimgUtility1
                this.imgUtility2 = this.build.bimgUtility2
                this.imgUtility3 = this.build.bimgUtility3
                this.imgElite = this.build.bimgElite
            },
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
    table {
        margin-left: auto;
        margin-right: auto;
    }
    .results {
        border-style: outset;
        border-color: cadetblue;
    }
    th {
        border-bottom-style: solid;
        border-bottom-color: cadetblue;
    }
    .seps {
        border-right-style: groove;
        border-right-color: cadetblue;
    }
</style>