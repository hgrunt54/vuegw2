<template>
    <div>
        <Profession :buildName="name" v-on:nameUpdate="onNameChange" :buildProf="prof" v-on:profUpdate="onProfChange" />
    </div>
    <div>
        <Skills :buildName="buildName" :buildProf="buildProf" />
    </div>
</template>

<script>
    import Profession from './Profession.vue'
    import Skills from './Skills.vue'

    export default {
        name: 'Create',
        components: {
            Profession,
            Skills,
        },
        data() {
            return {
                buildName: '',
                buildProf: '',
            }
        },
        methods: {
            onNameChange(value) {
                this.buildName = value
            },
            onProfChange(value) {
                this.buildProf = value
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
</style>