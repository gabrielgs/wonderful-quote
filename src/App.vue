<template>
  <div id="app">
    <div class="container">
      <h1>Quotes Added</h1>
      <app-progress :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-progress>
      <add-quote :quotes="quotes"></add-quote>
      <div class="columns is-multiline">
        <app-quotes v-for="quote in quotes"
          :quote="quote"
          :key="quote.id"></app-quotes>
      </div>
      <div class="columns">
        <div class="column">
          <div class="notification has-text-centered">
            Clik to delete a quote
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import appProgress  from './components/ProgressBar.vue'
  import addQuote from './components/AddQuote.vue'
  import appQuotes from './components/Quotes.vue'
  import { eventBus } from './main'

  export default {
    name: 'app',
    data () {
      return {
        quotes: [
          { id: 1, quote: 'The life is greatful'},
        ],
        maxQuotes: 10
      }
    },

    created() {
      eventBus.$on('addQuote', ( quote ) => {
        if ( this.quotes.length >= this.maxQuotes ) {
          return alert('Please delete a quote first')
        }

        this.quotes.push({
          id: quote.lastId + 1,
          quote: quote.quote
        })

        console.log(this.quotes)
      })

      eventBus.$on('deleteQuote', (quote) => {
        this.quotes = this.quotes.filter( element => {
          return element.id !== quote.id
        })
      })
    },

    components: {
      appProgress,
      addQuote,
      appQuotes
    }
  }
</script>

<style>
  .notification {
    background: #b2cbdb;
  }
</style>


