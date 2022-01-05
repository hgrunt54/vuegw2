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
            <img :src="skills.s1_Image" @click="hideSkillSelection(changeSkill, skills.s1)" />
            <img :src="skills.s2_Image" @click="hideSkillSelection(changeSkill, skills.s2)" />
            <img :src="skills.s3_Image" @click="hideSkillSelection(changeSkill, skills.s3)" />
            <img :src="skills.s4_Image" @click="hideSkillSelection(changeSkill, skills.s4)" />
        </p>
    </div>

    <div>
        <h2 style="text-align: center;">The Current Build Is:</h2>
        <p>Name: {{ buildName }}</p>
        <p>Profession: {{ buildProf }}</p>
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
        },
        data: function() {
            return {
                skills: {
                    heal: '',
                    utility1: '',
                    utility2: '',
                    utility3: '',
                    elite: '',
                    img_Heal: require('@/assets/images/skills/default/default_skill.png'),
                    img_Utility1: require('@/assets/images/skills/default/default_skill.png'),
                    img_Utility2: require('@/assets/images/skills/default/default_skill.png'),
                    img_Utility3: require('@/assets/images/skills/default/default_skill.png'),
                    img_Elite: require('@/assets/images/skills/default/default_skill.png'),

                    s1: '',
                    s1_Image: require('@/assets/images/skills/default/default_skill.png'),
                    s2: '',
                    s2_Image: require('@/assets/images/skills/default/default_skill.png'),
                    s3: 'default',
                    s3_Image: require('@/assets/images/skills/default/default_skill.png'),
                    s4: '',
                    s4_Image: require('@/assets/images/skills/default/default_skill.png'),
                },
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
                const t = { bName: this.buildName}
                fetch("http://localhost:5000/testPost", {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json;charset=utf-8',
                    },
                    body: JSON.stringify(t)
                })
                .then (response => response.json())
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