<template>
  <div id="app">
    <div class="container mx-auto mt-10 px-10">
      <div class="mx-auto">
        <app-QuoteProgress :quotes="quotes.length" />
      </div>
      <div class="mt-3 flex flex-col items-center">
        <div class="flex flex-col">
          <label class="font-semibold">Quote</label>
          <textarea
            placeholder="Type your wonderful quote"
            v-model="quote"
            class="mt-1 h-24 rounded outline-none focus:shadow-outline"
          />
        </div>
        <hr />

        <button
          class="mt-4 flex-none px-2 py-2 bg-blue-500 rounded font-medium text-white focus:outline-none focus:shadow-outline"
          @click="addQuote"
        >Add Quote</button>
      </div>

      <div class="mt-8 flex flex-wrap">
        <app-QuotesItem
          v-for="(quote, index) in quotes"
          :key="index"
          :quote="quote"
          :index="index"
          @delete-quote="removeQuote"
        />
      </div>
      <div class="mt-6 bg-blue-100 rounded py-4 text-center text-blue-700">
        <p>Info: Click on a Quote to delete it</p>
      </div>
    </div>
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" />
    <Destinations />-->
  </div>
</template>

<script>
// import HelloWorld from "./components/Tailwind/HelloWorld.vue";
// import Destinations from "./components/Tailwind/Destinations";
import QuoteProgress from "./components/QuoteProgress";
import QuotesItem from "./components/QuotesItem";
export default {
  name: "app",
  components: {
    // HelloWorld,
    // Destinations
    appQuoteProgress: QuoteProgress,
    appQuotesItem: QuotesItem
  },
  data() {
    return {
      quotes: ["Just a quote to have it here", "hello"],
      quote: null
    };
  },
  computed: {
    width() {
      return this.quotes.length * 10;
    }
  },
  methods: {
    addQuote() {
      if (this.quotes.length < 10 && this.quote) {
        this.quotes.push(this.quote);
        this.quote = null;
      } else if (this.quotes.length === 10) {
        alert("Delete a quote before adding  a new one!");
      }
    },
    removeQuote(index) {
      if (this.quotes.length > 1) {
        let newQuotes = this.quotes.slice();
        newQuotes.splice(index, 1);
        this.quotes = newQuotes;
      }
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
textarea {
  width: 500px;
}
</style>
