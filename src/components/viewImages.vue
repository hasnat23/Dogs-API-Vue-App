<template>
  <h1 v-if="this.results">{{ breedName }}</h1>
  <h2 v-if="!this.results">
    Click on the Breed List items to view the Results
  </h2>
  <div>
    <div class="row">
      <div
        class="col-3 col-md-3 col-sm-3"
        v-for="(result, index) in results"
        :key="index"
      >
        <img :src="result" />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "viewImages",
  props: {
    breeds: String,
  },
  data() {
    return {
      breedName: Object,
      results: null,
    };
  },
  updated() {
    this.breedName = this.breeds;
    console.log(this.breedName);
    this.fetchImages();
  },
  methods: {
    fetchImages() {
      try {
        axios
          .get("https://dog.ceo/api/breed/" + this.breedName + "/images")
          .then((response) => {
            this.results = response.data.message;
            console.log(this.results);
          });
      } catch (e) {
        console.log(e);
      }
    },
  },
};
</script>

<style scoped>
img {
  height: 200px;
  width: 300px;
  display: inline;
  object-fit: cover;
}
</style>
