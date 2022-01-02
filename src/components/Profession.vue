<template>
  <div class="Profession">
    <h1 class="h1">Create a Guild Wars 2 Build</h1>
    <label for="name">Name: </label>
      <input id="name" v-model="build.name" />
    <label for="sel_prof">Profession: </label>
      <select id="sel_prof" v-model="build.prof">
          <option disabled value>Please Select One</option>
          <option value="Mesmer">Mesmer</option>
          <option value="Necromancer">Necromancer</option>
      </select>
    <p>
        Build Name is: {{ this.build.name }}
    </p>
    <p>
        Selected Profession is: {{ this.build.prof }}
    </p>
  </div>
</template>

<script>
    export default {
        name: 'Profession',
        data() {
            return {
                build: {
                    name: '',
                    prof: '',
                    bgColor: '',
                }
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
