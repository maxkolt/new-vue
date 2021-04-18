<template>
    <div id="app">
        <section class="leftBlock">

            <img class="face" alt="foto" src="./assets/face.png"/>
            <ul class="menu">
                <li>ABOUT</li>
                <li>EXPERIENCE</li>
                <li>EDUCATION</li>
                <li>SKILLS</li>
                <li>BIO</li>
            </ul>
        </section>
        <section class="rightBloc">
            <h1 class="block">{{ firstName }}
                <span style="color: cadetblue">Koltovith</span>
            </h1>
            <a :href="linkUrl">My GitHub</a>
            <h5>
                <img alt="country" src="./assets/iconsCountry.png">
                Russia, Moscow
            </h5>
            <h5>
                <img alt="year" src="./assets/iconsYear.png">
                12 / 08 / 1991
            </h5>
            <h5 class="mail">
                <img alt="icons" src="./assets/iconsMail.png">
                {{ gmail }}
            </h5>

            <Weather
                    city="Minsk"
                    msg="Welcome to Your Vue.js App"/>

            <div class="click">
                <!--        <h1>{{ temperatura }}</h1>-->
                <!-- <button @click="weatherResponse">Ответ сервера</button> -->
            </div>
        </section>
    </div>

</template>

<script>
    import Weather from './components/Weather.vue'

    export default {
        name: 'App',
        components: {
            Weather,
        },
        data() {
            return {
                firstName: 'Maxim',
                gmail: '12345kolt@gmail.com',
                linkUrl: "https://github.com/maxkolt",
                serverData: null
            }
        },
        methods: {
            // getServer() {
            //  axios
            //    .get('https://www.foaas.com/cup/:Maxim')
            //  .then(response => (
            //    this.serverData = response.data.message
            // ));
            //},

        }
    }

    // clickCounter() {
    //   this.count = this.count + 1;
    // },

</script>

<style scoped>


    h5 {
        margin: 0;
    }

    .block {
        text-align: center;
        font-style: italic;
        font-family: Calibri;
        font-size: 65px;
        margin-right: 60%;
    }

    .face {
        border-radius: 100px;
        width: 150px;
        height: 150px;
        margin: 0 auto;
    }

    .mail {
        color: cadetblue;
    }

    .leftBlock {
        background-color: cadetblue;
    }

    .leftBlock {
        position: absolute;
        display: flex;
        flex-direction: column;
        width: 20%;
        text-align: center;
        justify-content: center;
        height: 98%;
    }

    .rightBloc {
        display: flex;
        flex-direction: column;
        position: relative;
        margin-left: 21%;
    }

    .menu {
        display: flex;
        flex-direction: column;
        list-style-type: none;
        padding: 0;
        line-height: 25px;
    }

    #app {
        font-family: "Avenir", Helvetica, Arial, sans-serif;
    }

    .click {
        display: flex;
        flex-direction: column;
        width: 10%;
    }

</style>
