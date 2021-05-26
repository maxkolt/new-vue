<template>
    <div class="hello">

        <div>
            <b-card
                    img-src=""
                    img-alt="Image"
                    img-top
                    tag="article"
                    style="max-width: 20rem;"
                    class="mb-2"
            >
                <b-card-text>
                    <h5>Имя первого питомца: </h5>
                    <br/>
                    <p>{{ krule.name }}</p>
<!--                    <h1>{{serverData.current.temperature}}</h1>-->
                    <!--                    <h3>{{ temperatura }}</h3>-->
                </b-card-text>
                <b-button @click="getDog">Узнать имя</b-button>
            </b-card>
        </div>
    </div>
</template>

<script>
    const axios = require('axios');
    export default {
        props: {
            // city: {
            //     type: String,
            //     required: true
            // }
        },
        data() {
            return {
                temperatura: '',
                accessKey: 'a54d1451af691342e975fde0186820bf',
                serverData: {},
                krule: {}
            }

        },
        created() {
            this.getWeatherFromRemoteServer();
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


            getWeatherFromRemoteServer() {
                axios.get(`http://api.weatherstack.com/current?access_key=${this.accessKey}&query=${this.city}`)
                    .then(response => {
                        this.serverData = response.data;
                        console.log('Ответ получен');
                        console.dir(this.serverData);
                    })
            }
            getWeatherFromRemoteServer() {
                axios.get(`http://api.weatherstack.com/current?access_key=${this.accessKey}&query=${this.city}`)
                    .then(response => {
                        this.serverData = response.data;
                        console.log('Ответ получен');
                        console.dir(this.serverData);
                    })
            }
        }
    }
</script>


<style scoped>
    .hello {
        margin: 0 auto;
    }

    .button {
        border-radius: 5px;
        border-radius: 5px;
    }
</style>
