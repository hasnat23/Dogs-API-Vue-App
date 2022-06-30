<template>
  <div class="row">
    <div class="col-3 col-md-3 col-sm-3">
      <breedList v-on:childToParent="onChildClick" />
    </div>
    <div class="col-9 col-md-9 col-sm-9">
      <view-images :breeds="breeds" />
    </div>
  </div>
</template>

<script>
import breedList from "./components/breedList.vue";
import viewImages from "./components/viewImages.vue";

export default {
  name: "App",
  components: {
    breedList,
    viewImages,
  },
  data() {
    return {
      breeds: null,
    };
  },
  methods: {
    onChildClick(value) {
      this.breeds = value;
    },
  },
};
</script>

<style>
.row {
  display: inline-block;
}
</style>
