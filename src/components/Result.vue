<template>
  <div class="resultContainer">
    <p>Reaction time: {{ score }}</p>
    <h5>{{feedback}}</h5>
  </div>
</template>

<script>
export default {
  name: "Result",
  props: ["score"],
  data() {
    return {
      feedback: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.feedback="Quick"
    }else {
      this.feedback="Slow"
    }
  },
};
</script>

<style>
.resultContainer {
  width: 200px;
  background-color: blanchedalmond;
  text-align: center;
  padding: 10px 30px;
  margin: 10px auto;
}
</style>