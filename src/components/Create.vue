<template>
    <div class="deets" style="visibility: hidden;">Section1</div>
    <div class="deets" style="border-style: inset;">
        <div>
            <Profession :buildName="name" v-on:nameUpdate="onNameChange" :buildProf="prof" v-on:profUpdate="onProfChange" />
        </div>
        <div>
            <ArmorWeapons />
        </div>
        <div>
            <Skills :buildName="buildName" :buildProf="buildProf" :buildSkills="defaultSkills" />
        </div>
        <div>
            <Traits />
        </div>
    </div>
    <div class="deets" style="border-style: outset;">
        <BuildDetails />
    </div>
</template>

<script>
    import Profession from './Profession.vue'
    import Skills from './Skills.vue'
    import Traits from './Traits.vue'
    import ArmorWeapons from './ArmorWeapons.vue'
    import BuildDetails from './CreateDetails.vue'

    export default {
        name: 'Create',
        components: {
            Profession,
            Skills,
            Traits,
            ArmorWeapons,
            BuildDetails,
        },
        data() {
            return {
                buildName: '',
                buildProf: '',
                defaultSkills: {
                    heal: "",
                    utility1: "",
                    utility2: "",
                    utility3: "",
                    elite: "",
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
            }
        },
        methods: {
            onNameChange(value) {
                this.buildName = value
            },
            onProfChange(value) {
                this.buildProf = value
                this.defaultSkills = {
                    heal: "",
                    utility1: "",
                    utility2: "",
                    utility3: "",
                    elite: "",
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
                }
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
    .deets {
        display: inline-block;
        float: left;
        width: 33%;
        border-style: solid;
        border-color: cadetblue;
    }
</style>