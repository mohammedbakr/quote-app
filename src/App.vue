<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <!-- can pass params in () -->
        <!-- <app-new @quoteAdded="newQuote($event)"></app-new> -->
        <!-- or dont want to cuz vue detect it automatically -->
        <app-new @quoteAdded="newQuote" ></app-new>
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="aler alert-info">
                    Info: Click on a Quote to delete it!
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import QuoteGrid from "./components/QuoteGrid.vue";
    import New from "./components/New.vue";
    import Header from "./components/Header.vue";

    export default {
        data() {
            return {
                quotes: [
                    'First Quote to show up',
                ],
                maxQuotes: 10,
            }
        },

        methods: {
            // quote is the value returned with the event
            // could be used without define it here
            newQuote(quote) {
                if (this.quotes.length >= this.maxQuotes) {
                    return alert('No more quotes!, Delete Some!')
                } else {
                    this.quotes.push(quote);
                }
            },

            deleteQuote(index) {
                this.quotes.splice(index, 1);
            }
        },

        components: {
            appQuoteGrid: QuoteGrid,
            appNew: New,
            appHeader: Header,
        }
    }
</script>

<style>
</style>
