<template>
  <section class="columns quote">
    <article class="column is-half is-offset-one-quarter has-text-centered">
      <b-field label="Quote">
        <b-input max-length="200"
          type="textarea"
          v-model="quote.quote"></b-input>
      </b-field>
      <button class="button is-primary"
        @click="addQuote">Add Quote</button>
    </article>
  </section>
</template>
<script>
  import { eventBus } from '../main'

  export default {
    props: ['quotes'],
    data: function () {
      return {
        quote: {
          cant: 1,
          percentage: 5,
          lastId: 0,
          quote: ''
        }
      }
    },
    methods: {
      addQuote() {
        this.quote.lastId = this.quotes[ this.quotes.length - 1 ].id
        eventBus.$emit('addQuote', this.quote)
      }
    }
  }
</script>


