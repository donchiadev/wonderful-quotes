<template>
  <div class="container">
    <app-quote-bar :quotesCurrent="quotes.length" :quotesLimit="quotesLimit"></app-quote-bar>
    <app-quote-form :addQuote="addQuote"></app-quote-form>
    <app-quote-list :quotes="quotes"></app-quote-list>
    <app-footer></app-footer>
  </div>
</template>

<script>
import { eventBus } from "./main";

import QuoteBar from "./components/QuoteBar.vue";
import QuoteForm from "./components/QuoteForm.vue";
import QuoteList from "./components/QuoteList.vue";
import Footer from "./components/Footer.vue";

export default {
  data() {
    return {
      quotesLimit: 10,
      idAvaiable: 5,
      quotes: [
        {
          id: 1,
          author: "Dr. Seuss",
          text: "Don't cry because it's over, smile because it happened."
        },
        {
          id: 2,
          author: "Oscar Wilde",
          text: "Be yourself; everyone else is already taken."
        },
        {
          id: 3,
          author: "Albert Einstein",
          text:
            "Two things are infinite: the universe and human stupidity; and I'm not sure about the universe."
        },
        {
          id: 4,
          author: "Marcus Tullius Cicero",
          text: "A room without books is like a body without a soul."
        }
      ]
    };
  },
  methods: {
    addQuote(author, text) {
      if (this.quotes.length < this.quotesLimit) {
        this.quotes.unshift({ id: this.idAvaiable, author, text });
        this.idAvaiable++;
      }
    }
  },
  components: {
    appQuoteBar: QuoteBar,
    appQuoteForm: QuoteForm,
    appQuoteList: QuoteList,
    appFooter: Footer
  },
  created() {
    eventBus.$on("removeQuote", quoteId => {
      this.quotes = this.quotes.filter(quote => quote.id !== quoteId);
    });
  }
};
</script>

<style>
body {
  background: #ecf0f1;
}
</style>
