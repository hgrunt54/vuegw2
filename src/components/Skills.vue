<template>
    <div class="Skills">
        <h1>Skills</h1>
        <button class="tooltip" value="skill.heal" @click="showSkillSelection('heal')">
            <span class="tooltiptext">{{ skills.heal }}</span>
            <img id="heal" :src="skills.img_Heal" />
            <p>Heal</p>
        </button>
        <button class="tooltip" value="skill.utility1" @click="showSkillSelection('utility1')">
            <span class="tooltiptext">{{ skills.utility1 }}</span>
            <img id="utility1" :src="skills.img_Utility1" />
            <p>Utility 1</p>
        </button>
        <button class="tooltip" value="skill.utility2" @click="showSkillSelection('utility2')">
            <span class="tooltiptext">{{ skills.utility2 }}</span>
            <img id="utility2" :src="skills.img_Utility2" />
            <p>Utility 2</p>
        </button>
        <button class="tooltip" value="skill.utility3" @click="showSkillSelection('utility3')">
            <span class="tooltiptext">{{ skills.utility3 }}</span>
            <img id="utility3" :src="skills.img_Utility3" />
            <p>Utility 3</p>
        </button>
        <button class="tooltip" value="skill.elite" @click="showSkillSelection('elite')">
            <span class="tooltiptext">{{ skills.elite }}</span>
            <img id="elite" :src="skills.img_Elite" />
            <p>Elite</p>
        </button>
    </div>

    <div class="skills_selection" v-show="skillSelection">
        Skill Selections
        <ul>
            <li class="tooltip"><img :src="skills.s1_Image" @click="hideSkillSelection(changeSkill, skills.s1)" />
                                <span class="tooltiptext">{{ skills.s1 }}</span></li>
            <li class="tooltip"><img :src="skills.s2_Image" @click="hideSkillSelection(changeSkill, skills.s2)" />
                                <span class="tooltiptext">{{ skills.s2 }}</span></li>
            <li class="tooltip"><img :src="skills.s3_Image" @click="hideSkillSelection(changeSkill, skills.s3)" />
                                <span class="tooltiptext">{{ skills.s3 }}</span></li>
            <li class="tooltip"><img :src="skills.s4_Image" @click="hideSkillSelection(changeSkill, skills.s4)" />
                                <span class="tooltiptext">{{ skills.s4 }}</span></li>
        </ul>
    </div>

    <div>
        <h2 style="text-align: center;">The Currently Selected Skills are:</h2>
        <p>Heal: {{ skills.heal }}</p>
        <p>Utility 1: {{ skills.utility1 }}</p>
        <p>Utility 2: {{ skills.utility2 }}</p>
        <p>Utility 3: {{ skills.utility3 }}</p>
        <p>Elite: {{ skills.elite }}</p>
    </div>
    <div>
        <button @click="save">Submit</button>
    </div>
</template>

<script>
    export default {
        name: 'Skills',
        props: {
            buildName: String,
            buildProf: String,
            buildSkills: {}
        },
        data: function() {
            return {
                skills: this.buildSkills,
                skillSelection: false,
                changeSkill: "",
                clickedSkill: "",
            };
        },
        methods: {
            showSkillSelection(sk) {
                let prof = this.buildProf;
                if (prof == 'Mesmer') {
                    this.skills.s1_Image = skill[0].img;
                    this.skills.s1 = skill[0].name;
                    this.skills.s2_Image = skill[1].img;
                    this.skills.s2 = skill[1].name;
                    this.skills.s3_Image = skill[2].img;
                    this.skills.s3 = skill[2].name;
                    this.skills.s4_Image = skill[3].img;
                    this.skills.s4 = skill[3].name;
                }
                else if (prof == 'Necromancer') {
                    this.skills.s1_Image = skill[4].img;
                    this.skills.s1 = skill[4].name;
                    this.skills.s2_Image = skill[5].img;
                    this.skills.s2 = skill[5].name;
                    this.skills.s3_Image = skill[6].img;
                    this.skills.s3 = skill[6].name;
                    this.skills.s4_Image = skill[7].img;
                    this.skills.s4 = skill[7].name;
                }
                this.skillSelection = true;
                this.changeSkill = sk;
            },
            hideSkillSelection(sk, sel) {
                for (let i = 0; i < skill.length; i++) {
                    if (sel == skill[i].name) {
                        if (sk == 'heal') {
                            this.skills.heal = skill[i].name;
                            this.skills.img_Heal = skill[i].img;
                        }
                        else if (sk == 'utility1') {
                            this.skills.utility1 = skill[i].name;
                            this.skills.img_Utility1 = skill[i].img;
                        }
                        else if (sk == 'utility2') {
                            this.skills.utility2 = skill[i].name;
                            this.skills.img_Utility2 = skill[i].img;
                        }
                        else if (sk == 'utility3') {
                            this.skills.utility3 = skill[i].name;
                            this.skills.img_Utility3 = skill[i].img;
                        }
                        else if (sk == 'elite') {
                            this.skills.elite = skill[i].name;
                            this.skills.img_Elite = skill[i].img;
                        }
                    }
                }
                return this.skillSelection = false;
            },
            save() {
                const build = {
                    "bName": this.buildName,
                    "bProf": this.buildProf,
                    "bHeal": this.skills.heal,
                    "bUtility1": this.skills.utility1,
                    "bUtility2": this.skills.utility2,
                    "bUtility3": this.skills.utility3,
                    "bElite": this.skills.elite,
                    "bimgHeal": this.skills.img_Heal,
                    "bimgUtility1": this.skills.img_Utility1,
                    "bimgUtility2": this.skills.img_Utility2,
                    "bimgUtility3": this.skills.img_Utility3,
                    "bimgElite": this.skills.img_Elite,
                }
                console.log(build);
                fetch("http://localhost:5000/buildCreate", {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json;charset=utf-8',
                    },
                    body: JSON.stringify(build)
                })
            }
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
        },
        {
            profession: 'Necromancer',
            name: 'Plague Signet',
            img: require('@/assets/images/skills/necromancer/utilities/Plague_Signet.png')
        },
        {
            profession: 'Necromancer',
            name: 'Signet of Spite',
            img: require('@/assets/images/skills/necromancer/utilities/Signet_of_Spite.png')
        },
        {
            profession: 'Necromancer',
            name: 'Signet of the Locust',
            img: require('@/assets/images/skills/necromancer/utilities/Signet_of_the_Locust.png')
        },
        {
            profession: 'Necromancer',
            name: 'Signet of Undeath',
            img: require('@/assets/images/skills/necromancer/utilities/Signet_of_Undeath.png')
        },
    ];
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

    .skillsSelect {
        visibility: hidden !important;
        position: relative;
    }
    .tooltip {
        position: relative;
        display: inline-block;
        border-bottom: 1px dotted black; /* If you want dots under the hoverable text */
    }
    /* Tooltip text */
        .tooltip .tooltiptext {
            visibility: hidden;
            width: 100px;
            bottom: 100%;
            left: 50%;
            margin-left: -50px;
            background-color: #008080;
            color: white;
            text-shadow: 2px 2px 5px black;
            text-align: center;
            padding: 5px 0;
            border-radius: 6px;
            /* Position the tooltip text - see examples below! */
            position: absolute;
            z-index: 1;
        }
    /* Show the tooltip text when you mouse over the tooltip container */
    .tooltip:hover .tooltiptext {
        visibility: visible;
    }
</style>