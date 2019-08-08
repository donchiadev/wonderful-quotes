<template>
  <div class="row">
    <div class="col">
      <form>
        <div class="form-group">
          <label for="author">Author</label>
          <input
            type="text"
            class="form-control"
            id="author-input"
            placeholder="Author"
            v-model="author"
          />
        </div>
        <div class="form-group">
          <label for="quote">Quote</label>
          <textarea
            class="form-control"
            id="quote-input"
            rows="6"
            placeholder="Quote"
            v-model="text"
          ></textarea>
        </div>
        <div style="text-align: center;">
          <button @click="addQuote(author, text)" type="button" class="btn btn-primary">Add Quote</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  props: ["addQuote"],
  data() {
    return {
      author: "",
      text: ""
    };
  }
};
</script>


<style scoped>
form {
  margin: 2.5em 0;
}

label {
  font-weight: 500;
}
</style>
