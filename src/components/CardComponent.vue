<template>
  <div class="card">
    Index:{{ value }} Visible:{{ visible }}
    <div></div>
    <div></div>
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
</style>
