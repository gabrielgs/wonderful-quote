<template>
  <div id="app">
    <div class="container">
      <h1>Quotes Added</h1>
      <app-progress></app-progress>
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
        ]
      }
    },

    created() {
      eventBus.$on('addQuote', ( quote ) => {
        this.quotes.push({
          id: quote.lastId + 1,
          quote: quote.quote
        })
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


