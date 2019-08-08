<template>
  <div class="row">
    <div class="col">
      <h2>Quotes Added</h2>
      <div id="statusBar">
        <div
          v-show="quotesCurrent >= 1"
          :style="progressStyleUpdate"
          id="progressStatus"
        >{{ quotesCurrent }} / {{ quotesLimit }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["quotesCurrent", "quotesLimit"],
  computed: {
    progressStyleUpdate() {
      return {
        width: this.quotesCurrent + "0%"
      };
    }
  }
};
</script>


<style scoped>
#statusBar {
  height: 2.5em;
  background: #d4dadf;
  border-radius: 0.25em;
}

#progressStatus {
  height: inherit;
  width: 0%;
  background: #3498db;
  border-radius: inherit;
  color: #ffffff;
  font-weight: 400;
  text-align: center;
  line-height: 2.4em;
}
</style>
