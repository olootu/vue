<template>
  <div class="film-item">
    <div @click="getDetails" class="flex-item">
      <div class="title">
        <p>Film Name: {{item.Title}}</p>
        <p>Year: {{item.Year}}</p>
      </div>

      <div class="image">
        <img v-bind:src="item.Poster" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FilmItem",
  props: ["item"],
  methods: {
    getDetails() {
      console.log("geting details");
      this.$emit("get-details", this.item.imdbID);
    }
  }
};
</script>

<style scoped>
.film-item {
  background: #222;
  padding: 10px;
  color: #aaa;
  overflow: hidden;
  margin-bottom: 20px;
}
.flex-item {
  display: flex;
  cursor: pointer;
}

.title {
  flex: 1;
}

.image {
  flex: 1;
}
.image img {
  width: 100%;
  max-width: 100%;
  height: auto;
}

.title p {
  display: block;
  font-size: 1.5em;
  margin-block-start: 0.83em;
  margin-block-end: 0.83em;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
  font-weight: bold;
  text-transform: uppercase;
}
</style>