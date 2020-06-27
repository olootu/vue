<template>
  <div>
    <Search v-on:search-film="searchFilm" />
    <h2 class="no-data" v-if="isEmpty">Sorry no result found...</h2>
    <Films v-on:fetch-detail="fetchDetails" v-bind:items="items" />
    <FilmDetails v-bind:itemsDetails="itemsDetails" />
  </div>
</template>

<script>
import Films from "../components/Films";
import Search from "../components/Search";
import FilmDetails from "../components/FilmDetails";
import axios from "axios";

export default {
  name: "Home",
  components: {
    Films,
    Search,
    FilmDetails
  },
  data() {
    return {
      items: [],
      itemsDetails: null,
      isEmpty: false
    };
  },
  methods: {
    searchFilm(title) {
      axios
        .get(`https://www.omdbapi.com/?s=${title}&apikey=a56adf1b`)
        .then(res => {
          if (res.data.Search) {
            this.items = res.data;
            this.isEmpty = false;
          } else {
            this.isEmpty = true;

            //to clear the view if there were items displayed before
            this.items = [];
          }
          this.itemsDetails = null;
        })
        .catch(err => console.log(err));
    },

    // Fetch Film Extra Details
    fetchDetails(id) {
      axios
        .get(`https://www.omdbapi.com/?i=${id}&apikey=a56adf1b`)
        .then(details => {
          this.itemsDetails = details.data;
          this.items = [];
        })
        .catch(err => console.log(err));
    }
  },

  created() {}
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.btn {
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
  border: none;
}

.btn:hover {
  background: #666;
}

.no-data {
  text-align: center;
}
</style>
