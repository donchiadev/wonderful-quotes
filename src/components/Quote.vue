<template>
  <div class="card quote" @click="removeQuote(quoteId)">
    <div class="card-body">
      <blockquote class="blockquote mb-0">
        <p class="quote-text">
          “
          <slot name="text"></slot>”
        </p>
        <footer class="blockquote-footer quote-author">
          <slot name="author">Unknown</slot>
        </footer>
      </blockquote>
    </div>
  </div>
</template>

<script>
import { eventBus } from "../main";

export default {
  props: ["quoteId"],
  methods: {
    removeQuote(quoteId) {
      eventBus.$emit("removeQuote", quoteId);
    }
  }
};
</script>

<style scoped>
.quote {
  margin: 1% 1%;
  height: inherit;
  width: 48%;
  display: inline-block;
  cursor: pointer;
}

.quote-text {
  font-family: "Indie Flower", cursive;
  font-size: 0.8em;
}

.quote-author {
  font-family: "Vollkorn", serif;
}
</style>

