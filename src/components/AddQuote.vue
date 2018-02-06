<template>
  <section class="columns quote">
    <article class="column is-half is-offset-one-quarter quote-add">
      <b-field label="Quote">
        <b-input max-length="200" type="textarea"></b-input>
      </b-field>
      <button class="button is-primary"
        @click="addQuote">Add Quote</button>
    </article>
  </section>
</template>
<script>
  import { eventBus } from '../main'

  export default {
    data: function () {
      return {
        quote: {
          cant: 1,
          percentage: 5
        }
      }
    },
    methods: {
      addQuote() {
        eventBus.$emit('addQuote', this.quote)
      }
    }
  }
</script>


