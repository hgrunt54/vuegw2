<template>
    <div class="Skills">
        <h1>Skills</h1>
        <button class="heal" value="skill.heal" @click="skillSelection = true">
            <img id="heal" src="@/assets/images/skills/default/default_skill.png" />
            <p>Heal</p>
        </button>
        <button class="utility" value="skill.utility1" @click="skillSelection = true">
            <img id="utility1" src="@/assets/images/skills/default/default_skill.png" />
            <p>Utility 1</p>
        </button>
        <button class="utility" value="skill.utility2" @click="skillSelection = true">
            <img id="utility2" src="@/assets/images/skills/default/default_skill.png" />
            <p>Utility 2</p>
        </button>
        <button class="utility" value="skill.utility3" @click="skillSelection = true">
            <img id="utility3" src="@/assets/images/skills/default/default_skill.png" />
            <p>Utility 3</p>
        </button>
        <button class="elite" value="skill.elite" @click="skillSelection = true">
            <img id="elite" src="@/assets/images/skills/default/default_skill.png" />
            <p>Elite</p>
        </button>
    </div>

    <div class="tooltip-container">
        <slot />
        <div class="tooltip">
            <span class="text">{{ text }}</span>
        </div>
    </div>

    <div class="skills_selection" v-show="skillSelection">
        Skill Selections
        <p>
            <img src="@/assets/images/skills/default/default_skill.png" @click="skillSelection = false" />
            <img src="@/assets/images/skills/default/default_skill.png" @click="skillSelection = false" />
            <img id="heal" src="@/assets/images/skills/default/default_skill.png" @click="skillSelection = false" />
        </p>
        <p>
            <img src="@/assets/images/skills/default/default_skill.png" @click="skillSelection = false" />
            <img src="@/assets/images/skills/default/default_skill.png" @click="skillSelection = false" />
            <img id="heal" src="@/assets/images/skills/default/default_skill.png" @click="skillSelection = false" />
        </p>
        <p>
            <img src="@/assets/images/skills/default/default_skill.png" @click="skillSelection = false" />
            <img src="@/assets/images/skills/default/default_skill.png" @click="skillSelection = false" />
            <img src="@/assets/images/skills/default/default_skill.png" @click="skillSelection = false" />
        </p>
    </div>
</template>

<script>
    export default {
        name: 'Skills',
        data() {
            return {
                skills: {
                    heal: 'default',
                    utility1: 'default',
                    utility2: 'default',
                    utility3: 'default',
                    elite: 'default',
                },
                skillSelection: false,
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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

    .skillsSelect {
        visibility: hidden !important;
        position: relative;
    }
</style>