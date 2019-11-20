<template>
  <div
    class="quote text-2xl px-4 py-2 border-gray-400 border rounded mb-3 hover:bg-red-200 cursor-pointer w-64 mb-4 mr-4 h-24"
    @click="remove"
  >
    <p>{{ quote }}</p>
  </div>
</template>

<script>
// import { eventBus } from "../main";
export default {
  name: "Quotes-item",
  props: ["quote", "index"],
  methods: {
    remove() {
      this.$emit("delete-quote", this.index);
    }
  }
};
</script>

<style scoped>
.quote {
  font-family: "Arizonia", cursive;
}
</style>