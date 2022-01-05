<template>
    <div style="text-align: center; background-color: cadetblue">
        <button @click='actCreate'>Create Build</button>
        <button @click='actFind'>Find Build</button>
    </div>
    <div>
        <p>{{ greeting }}</p>
        <p>From Flask: {{ flaskGreeting }}</p>
    </div>
    <div v-if="createActive">
        <create />
    </div>
    <div v-if="findActive">
        <find />
    </div>
</template>

<script>
    import Create from './components/Create.vue'
    import Find from './components/Find.vue'

export default {
    name: 'App',
        components: {
            Create,
            Find,
        },
        data: function() {
            return {
                createActive: true,
                findActive: false,
                greeting: 'Hello, Vue!',
                flaskGreeting: '',
            }
        },
        methods: {
            actCreate() {
                this.createActive = true;
                this.findActive = false;
            },
            actFind() {
                this.createActive = false;
                this.findActive = true;
            }
        },
        created: async function () {
            const routes = await fetch("http://localhost:5000/greeting");
            const gObject = await routes.json();
            this.flaskGreeting = gObject.Greeting;
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
}
</style>
