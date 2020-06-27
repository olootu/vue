<template>
  <div class="flex-item">
    <div class="item" v-bind:key="result.id" v-for="result in items.Search">
      <FilmItem v-on:get-details="getDetails" v-show="result" v-bind:item="result" />
    </div>
  </div>
</template>

<script>
import FilmItem from "./FilmItem";
export default {
  name: "Films",
  components: {
    FilmItem
  },
  props: ["items"],
  methods: {
    getDetails(id) {
      console.log(id);
      this.$emit("fetch-detail", id);
    }
  }
};
</script>

<style scoped>
.flex-item {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  padding: 0 10px;
}

.item {
  width: 33%;
  margin-bottom: 20px;
  background: #222;
  min-height: 300px;
  overflow: hidden;
  cursor: pointer;
}
</style>