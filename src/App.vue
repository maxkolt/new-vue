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

            <Dog :city="currentCity" msg="Welcome to Your Vue.js App"/>
            <Dog city="Moscow" msg="Welcome to Your Vue.js App"/>
            <b-button @click="getDog">Узнать имя</b-button>

            <div id="demo">
                <button v-on:click="show = !show">
                    Переключить
                </button>
                <transition name="fade">
                    <p v-if="show">привет</p>
                </transition>
            </div>

            <div class="click">

                <!--                 <button @click="">Ответ сервера</button> -->
            </div>
            <div col-3>
                <input type="date" class="form-control">
                <input type="date" class="form-control">
            </div>
        </section>
    </div>

</template>

<script>
    import Dog from './components/Dog.vue'

    export default {
        name: 'App',
        components: {
            Dog,
        },
        data() {
            return {
                show: true,
                currentCity: 'Minsk',
                firstName: 'Maxim',
                gmail: '12345kolt@gmail.com',
                linkUrl: "https://github.com/maxkolt",
                serverData: null
            }
        },
        methods: {
            getDog: function () {
                fetch('../dog1.json')
                    .then(
                        response => {
                            response.json().then(data => {
                                console.log(data);
                            });
                        }
                    )
                    .catch(err => console.log('Fetch Error :-S', err));
            },






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

    .fade-enter-active, .fade-leave-active {
        transition: opacity .5s;
    }

    .fade-enter, .fade-leave-to
    {
        opacity: 0;
    }

</style>
