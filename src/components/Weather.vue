<template>
    <div class="hello">

        <div>
            <b-card
                    :title="city"
                    img-src=""
                    img-alt="Image"
                    img-top
                    tag="article"
                    style="max-width: 20rem;"
                    class="mb-2"
            >
                <b-card-text>
                    <h1>{{serverData.current.temperature}}</h1>
                    <!--                    <h3>{{ temperatura }}</h3>-->
                </b-card-text>
                <b-button href="#" variant="primary">Узнать погоду</b-button>
            </b-card>
        </div>
    </div>
</template>

<script>
    const axios = require('axios');
    export default {
        props: {
            city: {
                type: String,
                required: true
            }
        },
        data() {
            return {
                temperatura: '',
                accessKey: 'a54d1451af691342e975fde0186820bf',
                serverData: {}
            }

        },
        created() {
            this.getWeatherFromRemoteServer();
        },

        methods: {
            getDog() {
                fetch('./api/some.json')
                    .then(
                        response => {
                            if (response.status !== 200) {
                                console.log('Looks like there was a problem. Status Code: ' +
                                    response.status);
                                return;
                            }

                            // Examine the text in the response
                            response.json().then(data => {
                                console.log(data);
                            });
                        }
                    )
                    .catch(err => {
                        console.log('Fetch Error :-S', err);
                    });
            },


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
