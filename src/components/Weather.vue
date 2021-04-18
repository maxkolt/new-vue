<template>
    <div class="hello">

        <div>
            <b-card
                    title="Card Title"
                    img-src=""
                    img-alt="Image"
                    img-top
                    tag="article"
                    style="max-width: 20rem;"
                    class="mb-2"
            >
                <b-card-text>
                    <h3>{{ temperatura }}</h3>
                </b-card-text>
                <b-button href="#" variant="primary">Узнать погоду</b-button>
            </b-card>
        </div>
    </div>
</template>

<script>
    const axios = require('axios');
    export default {
        name: 'HelloWorld',
        data() {
            return {
                temperatura: '',
                accessKey: 'a54d1451af691342e975fde0186820bf',
                serverData: {},
            }

        },
        created() {
            this.getWeatherFromRemoteServer();
        },

        methods: {
            getWeatherFromRemoteServer() {
                let city = `Minsk`;
                axios.get(`http://api.weatherstack.com/current?access_key=${this.accessKey}&query=${city}`)
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
    }
</style>
