<template>
  <div class="card" @click="cardChoice">
    <div class="header" v-if="visible">{{ name }}</div>
    <div class="body is-front" v-if="visible">
      <img :src="`${value}`" class="dog" />
    </div>
    <div class="body is-back" v-else>
      <img src="../../public/images/dog.png" />
    </div>
    <div class="footer" v-if="visible">
      <a class="api" href="https://dog.ceo/dog-api/" target="_blank">DOG API</a>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      required: true,
    },
    position: {
      type: Number,
      required: true,
    },
    visible: {
      type: Boolean,
      default: false,
    },
    name: {
      type: String,
      required: true,
    },
  },
  setup(props, context) {
    const cardChoice = () => {
      context.emit("card-choice", {
        position: props.position,
        value: props.value,
        name: props.name,
      });
    };
    return {
      cardChoice,
    };
  },
};
</script>

<style>
.card {
  height: 280px;
  width: 280px;
  border: 7px solid gray;
  border-radius: 5%;
  margin: auto;
}
.header {
  display: block;
  border-bottom: 4px solid gray;
  height: 20px;
  padding: 2px;
}
.body {
  height: 100%;
  background-size: cover;
  border-radius: 3%;
  display: flex;

  align-items: center;
  justify-content: center;
}
.body .is-back {
  height: 100%;
  background-size: cover;
}
.body.is-front {
  height: 220px;
  background-size: cover;
}
img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  transform: scale(1, 1);
}

.is-front {
  background-size: cover;
}
.is-back {
  background-color: turquoise;
  background-size: cover;
}
.footer {
  display: block;
  border-top: 4px solid gray;
  height: 20px;
}
.api {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 5px;
}
</style>
