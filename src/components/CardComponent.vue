<template>
  <div class="card" @click="cardChoice">
    <div class="header" v-if="visible">
      Index:{{ value }} Visible:{{ visible }}
    </div>
    <div class="body is-front" v-if="visible"></div>
    <div class="body is-back" v-else>
      <img src="../../public/images/dog.png" />
    </div>
    <div class="footer" v-if="visible"></div>
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
  },
  setup(props, context) {
    const cardChoice = () => {
      context.emit("card-choice", {
        position: props.position,
        value: props.value,
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
  height: 300px;
  width: 300px;
  border: 4px solid gray;
  border-radius: 5%;
  margin-left: 30px;
  margin-right: 30px;
}
.header {
  display: block;
  border-bottom: 4px solid gray;
  height: 50px;
}
.body {
  height: 100%;
  background-size: cover;
  display: flex;
  align-items: center;
  justify-content: center;
}
.body .is-back {
  height: 100%;
  background-size: cover;
}
.body.is-front {
  height: 200px;
}
.is-front {
  background-color: magenta;
  background-size: cover;
}
.is-back {
  background-color: turquoise;
  background-size: cover;
}
.footer {
  display: block;
  border-top: 4px solid gray;
  height: 50px;
}
</style>
