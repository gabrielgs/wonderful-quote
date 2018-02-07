<template>
  <div class="column">
    <progress class="progress is-info"  :value="quoteCount" max="10"></progress>
    <span :style="{ left: `${left}%` }"
      v-if="quoteCount > 0">{{ quoteCount }} / {{ maxQuotes }}</span>
  </div>
</template>
<script>
  import { eventBus } from '../main'
  export default {
    props: ['quoteCount', 'maxQuotes'],
    data: function () {
      return {
        left: 5
      }
    },
    created() {
      eventBus.$on('addQuote', (item) => {
        if ( this.quoteCount < this.maxQuotes ) {
          this.left += 5
        }
      })

      eventBus.$on('deleteQuote', () => {
        this.left -= 5
      })
    }
  }
</script>
<style scoped>
  div {
    position: relative;
  }

  .progress {
    margin: 0;
  }

  .progress::-webkit-progress-value {
    transition: width 0.5s ease;
  }

  span {
    color: #fff;
    position: absolute;
    top: 20%;
  }
</style>


