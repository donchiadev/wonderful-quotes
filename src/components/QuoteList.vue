<template>
  <div class="row">
    <div class="col quote-list">
      <app-quote v-for="quote in quotes" :quoteId="quote.id" :key="quote.id">
        <template v-slot:text>{{ quote.text }}</template>
        <template v-if="quote.author" v-slot:author>{{ quote.author }}</template>
      </app-quote>
    </div>
  </div>
</template>

<script>
import Quote from "./Quote.vue";

export default {
  props: ["quotes"],
  components: {
    appQuote: Quote
  }
};
</script>

<style scoped>
.quote-list {
  margin: 1.5em 0;
}
</style>
