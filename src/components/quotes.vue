<template>
    <div>
        <button class="btn btn-primary" @click="onGetQuotes">Get Quotes</button>
        <hr>
        <app-quote v-for="quote in quotes" :qt="quote"></app-quote>
    </div>
</template>

<script>
import Quote from './quote.vue';
import axios from 'axios';

    export default {
        data() {
            return {
                quotes: []
            }
        },
        methods: {
            onGetQuotes() {
                axios.get('http://localhost:8000/api/quotes')
                    .then(response => {
                        //console.log(response);
                        this.quotes = response.data.quotes;
                    })
                    .catch(error => console.log(error));
            }
        },
        components: {
            'app-quote': Quote
        }
    }
</script>