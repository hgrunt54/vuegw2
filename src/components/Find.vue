<template>
    <h1 class="h1">Find a Guild Wars 2 Build</h1>
    <label for="sel_prof"> Profession: </label>
    <select id="sel_prof" v-model='prof' v-on:change="profChange">
        <option disabled value>Please Select One</option>
        <option value="All">All Builds</option>
        <option value="Mesmer">Mesmer</option>
        <option value="Necromancer">Necromancer</option>
    </select>
    <button @click="showResults"> Search </button>
    <button @click="clearResults"> Clear Results</button>
    <p></p>
    <table id="tblResults" class="results">
        <th>Name </th>
        <th>Profession </th>
        <th>Heal </th>
        <th>Utility 1 </th>
        <th>Utility 2 </th>
        <th>Utility 3 </th>
        <th>Elite </th>
        <tr v-for="td in tds" :key="td">
            <td class="seps">{{ td.Name }}</td>
            <td class="seps">{{ td.Prof }}</td>
            <td>
                <img :src="td.imgHeal" alt="None"/>
                <p>{{ td.Heal }}</p>
            </td>
            <td>
                <img :src="td.imgUtility1" alt="None"/>
                <p>{{ td.Utility1 }}</p>
            </td>
            <td>
                <img :src="td.imgUtility2" alt="None"/>
                <p>{{ td.Utility2 }}</p>
            </td>
            <td>
                <img :src="td.imgUtility3" alt="None"/>
                <p>{{ td.Utility3 }}</p>
            </td>
            <td>
                <img :src="td.imgElite" />
                <p>{{ td.Elite }}</p>
            </td>
        </tr>
    </table>
</template>

<script>
    export default {
        name: 'Find',
        data() {
            return {
                build: [],
                td: {
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
                },
                tds: []
            }
        },
        created: async function () {
            const routes = await fetch("http://localhost:5000/buildQuery");
            const gObject = await routes.json();
            this.build = JSON.parse(gObject);
            console.log(this.build);
            
        },
        methods: {
            showResults() {
                this.tds = []
                let b = this.build;
                console.log("b is: " + b)
                for (let i = 0; i < b.length; i++) {
                    console.log(i)
                    console.log(b[i])
                    const td = {
                        Name: b[i].bName,
                        Prof: b[i].bProf,
                        Heal: b[i].bHeal,
                        Utility1: b[i].bUtility1,
                        Utility2: b[i].bUtility2,
                        Utility3: b[i].bUtility3,
                        Elite: b[i].bElite,
                        imgHeal: b[i].bimgHeal,
                        imgUtility1: b[i].bimgUtility1,
                        imgUtility2: b[i].bimgUtility2,
                        imgUtility3: b[i].bimgUtility3,
                        imgElite: b[i].bimgElite,
                    }
                    console.log(b[i].Name)
                    this.tds.push(td)
                }
            },
            clearResults() {
                this.tds = []
            }
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
</style>