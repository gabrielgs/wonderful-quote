<template>
  <div id="app">
    <div class="container">
      <h1>Quotes Added</h1>
      <progressBar></progressBar>
      <add-quote></add-quote>
      <div class="columns is-multiline">
        <quotes v-for="quote in 8"></quotes>
      </div>
    </div>
  </div>
</template>

<script>
  import progressBar  from './components/ProgressBar.vue'
  import addQuote from './components/AddQuote.vue'
  import quotes from './components/Quotes.vue'

  export default {
    name: 'app',
    data () {
      return {
        msg: 'Welcome to Your Vue.js App'
      }
    },

    components: {
      progressBar,
      addQuote,
      quotes
    }
  }
</script>

