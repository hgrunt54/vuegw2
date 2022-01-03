<template>
    <div class="Skills">
        <h1>Skills</h1>
        <button class="heal" value="skill.heal" @click="showSkillSelection('heal')">
            <img id="heal" :src="skills.img_Heal" />
            <p>Heal</p>
        </button>
        <button class="utility" value="skill.utility1" @click="showSkillSelection('utility1')">
            <img id="utility1" :src="skills.img_Utility1" />
            <p>Utility 1</p>
        </button>
        <button class="utility" value="skill.utility2" @click="showSkillSelection('utility2')">
            <img id="utility2" :src="skills.img_Utility2" />
            <p>Utility 2</p>
        </button>
        <button class="utility" value="skill.utility3" @click="showSkillSelection('utility3')">
            <img id="utility3" :src="skills.img_Utility3" />
            <p>Utility 3</p>
        </button>
        <button class="elite" value="skill.elite" @click="showSkillSelection('elite')">
            <img id="elite" :src="skills.img_Elite" />
            <p>Elite</p>
        </button>
    </div>

    <div class="skills_selection" v-show="skillSelection">
        Skill Selections
        <p>
            <img src="@/assets/images/skills/mesmer/utilities/Signet_of_Domination.png" @click="hideSkillSelection(this.changeSkill, 'Signet of Domination')" />
            <img src="@/assets/images/skills/mesmer/utilities/Signet_of_Illusions.png" @click="hideSkillSelection(this.changeSkill, 'Signet of Illusions')" />
            <img src="@/assets/images/skills/mesmer/utilities/Signet_of_Inspiration.png" @click="hideSkillSelection(this.changeSkill, 'Signet of Inspiration')" />
            <img src="@/assets/images/skills/mesmer/utilities/Signet_of_Midnight.png" @click="hideSkillSelection(this.changeSkill, 'Signet of Midnight')" />
        </p>
    </div>

    <div>
        <h2 style="text-align: center;">The Currently Selected Skills are:</h2>
        <p>Heal: {{ this.skills.heal }}</p>
        <p>Utility 1: {{ this.skills.utility1 }}</p>
        <p>Utility 2: {{ this.skills.utility2 }}</p>
        <p>Utility 3: {{ this.skills.utility3 }}</p>
        <p>Elite: {{ this.skills.elite }}</p>
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
                    img_Heal: require('@/assets/images/skills/default/default_skill.png'),
                    img_Utility1: require('@/assets/images/skills/default/default_skill.png'),
                    img_Utility2: require('@/assets/images/skills/default/default_skill.png'),
                    img_Utility3: require('@/assets/images/skills/default/default_skill.png'),
                    img_Elite: require('@/assets/images/skills/default/default_skill.png'),
                },
                skillSelection: false,
                changeSkill: ""
            };
        },
        methods: {
            showSkillSelection(sk) {
                this.skillSelection = true;
                this.changeSkill = sk;
            },
            hideSkillSelection(sk, sel) {
                for (let i = 0; i < skill.length; i++) {
                    if (sel == skill[i].name) {
                        if (sk == 'heal') {
                            this.skills.heal = skill[i].name;
                            this.skills.img_Heal = skill[i].img;
                            this.skillSelection = false;
                        }
                        else if (sk == 'utility1') {
                            this.skills.utility1 = skill[i].name;
                            this.skills.img_Utility1 = skill[i].img;
                            this.skillSelection = false;
                        }
                        else if (sk == 'utility2') {
                            this.skills.utility2 = skill[i].name;
                            this.skills.img_Utility2 = skill[i].img;
                            this.skillSelection = false;
                        }
                        else if (sk == 'utility3') {
                            this.skills.utility3 = skill[i].name;
                            this.skills.img_Utility3 = skill[i].img;
                            this.skillSelection = false;
                        }
                        else if (sk == 'elite') {
                            this.skills.elite = skill[i].name;
                            this.skills.img_Elite = skill[i].img;
                            this.skillSelection = false;
                        }
                    }
                }
            },
        }
    }

    const skill = [
        {
            profession: 'Mesmer',
            type: 'utility',
            name: 'Signet of Domination',
            img: require('@/assets/images/skills/mesmer/utilities/Signet_of_Domination.png')
        },
        {
            profession: 'Mesmer',
            type: 'utility',
            name: 'Signet of Illusions',
            img: require('@/assets/images/skills/mesmer/utilities/Signet_of_Illusions.png')
        },
        {
            profession: 'Mesmer',
            type: 'utility',
            name: 'Signet of Inspiration',
            img: require('@/assets/images/skills/mesmer/utilities/Signet_of_Inspiration.png')
        },
        {
            profession: 'Mesmer',
            type: 'utility',
            name: 'Signet of Midnight',
            img: require('@/assets/images/skills/mesmer/utilities/Signet_of_Midnight.png')
        }
    ];
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