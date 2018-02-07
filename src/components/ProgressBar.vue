<template>
  <div class="column">
    <progress class="progress is-info"  :value="quotes" max="10" data-label="1/10"></progress>
    <span :style="{ left: `${left}%` }">{{ quotes }}/10</span>
  </div>
</template>
<script>
  import { eventBus } from '../main'
  export default {
    data: function () {
      return {
          quotes: 1,
          left: 5
      }
    },
    created() {
      eventBus.$on('addQuote', (item) => {
        this.quotes += item.cant
        this.left += item.percentage
      })

      eventBus.$on('deleteQuote', () => {
        this.quotes -= 1
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
    transition: all 1s ease
  }

  span {
    color: #fff;
    position: absolute;
    top: 20%;
  }
</style>


