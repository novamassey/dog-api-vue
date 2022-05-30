<template>
  <h1>Dog API</h1>
  <section class="container">
    <CardComponent
      v-for="(card, index) in cardArray"
      :key="index"
      :position="index"
      :value="card.value"
      :visible="card.visible"
      :name="card.name"
      @card-choice="toggleCard"
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
    };
  },
  mounted() {
    this.createCards();
  },
  methods: {
    createCards() {
      for (let i = 0; i < 10; i++) {
        this.cardArray.push({
          value: "",
          visible: false,
          position: i,
          name: "",
        });
      }
    },
    async toggleCard(payload) {
      await axios
        .get("https://dog.ceo/api/breeds/image/random")
        .then((response) => {
          this.dog = response.data;

          try {
            this.cardArray[payload.position].value = this.dog.message;
            this.cardArray[payload.position].visible = true;

            const url = new URL(this.dog.message);
            const path = url.pathname.substring(8);
            const breed = path.split("/");
            this.cardArray[payload.position].name = breed[0].toUpperCase();

            setTimeout(() => {
              this.cardArray[payload.position].visible = false;
            }, 2000);
          } catch (error) {
            console.log(error.message);
          }
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
  row-gap: 40px;
  margin: 0 auto;
}
</style>
