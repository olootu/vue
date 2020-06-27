<template>
  <div>
    <div class="film-details" v-if="itemsDetails">
      <h2 class="title">{{itemsDetails.Title}}</h2>
      <p>
        <label class="labels">Actors:</label>
        {{itemsDetails.Actors}}
      </p>
      <p>
        <label class="labels">Awards:</label>
        {{itemsDetails.Awards}}
      </p>

      <p>
        <label class="labels">Director:</label>
        {{itemsDetails.Director}}
      </p>
      <p>
        <label class="labels">Genre:</label>
        {{itemsDetails.Genre}}
      </p>

      <p>
        <label class="labels">Year:</label>
        {{itemsDetails.Year}}
      </p>
      <p>
        <label class="labels">ID:</label>
        {{itemsDetails.imdbID}}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "FilmDetails",
  props: {
    itemsDetails: Object
  }
};
</script>

<style scoped>
.film-details {
  background: #444;
  width: 85%;
  margin: 0 auto;
  color: #fff;
  padding: 10px;
}

.labels {
  font-weight: 900;
  padding-right: 20px;
  width: 5em;
  display: inline-block;
}

.title {
  text-align: center;
  text-transform: uppercase;
}

p:nth-of-type(even) {
  background: #666;
}

p {
  padding: 10px 5px;
}
</style>
