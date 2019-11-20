<template>
  <div>
    <h1 class="font-semibold">Quotes added</h1>
    <div
      class="progress-bar h-5 bg-blue-500 rounded text-white text-center"
      :style="{width: quotes * 10 + '%'}"
    >
      <span>{{quotes}}/10</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "QuoteProgress",
  props: ["quotes"]
};
</script>

<style scoped>
.progress-bar {
  width: 10%;
  transition: width 500ms;
}
</style>