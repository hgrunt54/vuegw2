<template>
    <Profession :buildName="name" v-on:nameUpdate="onNameChange" :buildProf="prof" v-on:profUpdate="onProfChange" />
    <Skills :buildName="buildName" :buildProf="buildProf"/>
</template>

<script>
    import Profession from './components/Profession.vue'
    import Skills from './components/Skills.vue'

export default {
    name: 'App',
        components: {
            Profession,
            Skills
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

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
