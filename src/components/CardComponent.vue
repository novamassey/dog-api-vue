<template>
  <div class="card">
    <div class="header">Index:{{ value }} Visible:{{ visible }}</div>
    <div class="body" v-if="visible"></div>
    <div class="body" v-else></div>
    <div class="footer"></div>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: Number,
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
  height: 200px;
}
.footer {
  display: block;
  border-top: 4px solid gray;
  height: 50px;
}
</style>
