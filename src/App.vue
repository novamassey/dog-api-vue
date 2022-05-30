<template>
  <h1>Dog API</h1>
  <button @click="fetchData">Get Dog</button>
  <section class="container">
    <CardComponent
      v-for="(card, index) in cardArray"
      :key="index"
      :position="index"
      :value="card.value"
      :visible="card.visible"
    />
  </section>
</template>

<script>
import axios from "axios";
import CardComponent from "./components/CardComponent.vue";
export default {
  name: "App",
  components: { CardComponent },
  data() {
    return {
      dog: {},
      cardArray: [],
      dogImage: "",
    };
  },
  mounted() {
    this.createCards();
  },
  methods: {
    createCards() {
      for (let i = 0; i < 10; i++) {
        this.cardArray.push({ value: i, visible: false, position: i });
        console.log("cardArray", this.cardArray);
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
.container {
  display: grid;
  grid-template-columns: repeat(5, 300px);
  grid-template-rows: repeat(2, 300px);
  column-gap: 30px;
  row-gap: 30px;
  justify-content: center;
}
</style>
