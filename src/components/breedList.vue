<template>
  <div>
    <h1>Breed List</h1>
    <ul v-for="(breed, index) of breeds" :key="index">
      <li
        @click="updateSelected(index)"
        :class="{ active: index == activeIndex }"
      >
        {{ index }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "breedList",
  data() {
    return {
      breeds: null,
      activeIndex: null,
    };
  },
  async created() {
    try {
      axios.get("https://dog.ceo/api/breeds/list/all").then((response) => {
        this.breeds = response.data.message;
        console.log(this.breeds);
      });
    } catch (e) {
      console.log(e);
    }
  },
  methods: {
    updateSelected(index) {
      this.$emit("childToParent", index);
      this.activeIndex = index;
    },
  },
};
</script>

<style scoped>
li {
  list-style: none;
}
.active {
  color: red;
  background-color: yellow;
}
</style>
