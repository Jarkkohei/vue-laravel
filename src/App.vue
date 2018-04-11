<template>
    <div id="app">
        <div class="container">
            <div class="row">
                <div class="col-xs-12">
                    <app-new-quote></app-new-quote>
                </div>
            </div>
        </div>
  </div>
</template>

<script>
    import NewQuote from './components/new-quote.vue';

    export default {
        data () {
            return {

            }
        },
        components: {
            'app-new-quote': NewQuote
        }
    }
</script>

<style>

</style>
