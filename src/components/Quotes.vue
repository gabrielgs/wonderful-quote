<template>
  <div class="column is-one-quarter">
    <div class="card quote-card"
      @click="deleteQuote">
      <div class="card-content">
        {{ quote.quote }}
      </div>
    </div>
  </div>
</template>

<script>
  import { eventBus } from '../main'

  export default {
    props: ['quote'],
    data: function () {
      return {
        selectedQuote: null
      }
    },

    methods: {
      deleteQuote() {
        this.selectedQuote = {
          id: this.quote.id,
          quote: this.quote.quote
        }

        eventBus.$emit('deleteQuote', this.selectedQuote)
      }
    }
  }
</script>


<style>
  .quote-card {
    width: 250px;
    height: auto;
    font-size: 1.5em;
    cursor: pointer;
    overflow-wrap: break-word;
  }

  .quote-card:hover {
    background-color: hsl(357, 70%, 75%);
  }
</style>

