<template>
  <h1>Dog API</h1>
  <button @click="fetchData">Get Dog</button>
</template>

<script>
import axios from "axios";
export default {
  name: "App",
  components: {},
  data() {
    return {
      dog: {},
      cardArray: [],
    };
  },
  mounted() {
    this.createCards();
  },
  methods: {
    createCards() {
      for (let i = 0; i < 11; i++) {
        this.cardArray.push(i);
        console.log(this.cardArray);
      }
    },
    fetchData() {
      axios.get("https://dog.ceo/api/breeds/image/random").then((response) => {
        this.dog = response.data;
        console.log(this.dog);
      });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
