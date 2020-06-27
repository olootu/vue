<template>
  <div class="search-film">
    <form @submit="searchFilmTitle">
      <input v-model="title" type="text" name="title" placeholder="Search films by title..." />
      <input type="submit" class="btn" value="Search" />
    </form>
  </div>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    searchFilmTitle(e) {
      e.preventDefault();
      this.$emit("search-film", this.title);
      this.title = "";
    }
  }
};
</script>

<style>
.search-film {
  padding: 25px 10px;
}
form {
  display: flex;
}

input[type="text"] {
  flex: 10;
  font-size: 20px;
}

input[type="submit"] {
  flex: 2;
}

input {
  padding: 20px;
}
</style>
