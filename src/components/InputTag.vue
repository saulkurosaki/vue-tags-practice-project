<script>
export default {
  data() {
    return {
      currentValue: "",
      tags: [],
    };
  },

  methods: {
    handleKeyDown(e) {
      if (e.key === "Enter" && this.currentValue !== "") {
        this.tags.push(this.currentValue);
      }
    },
  },
};
</script>

<template>
  <div class="inputTag">
    <div class="tags">
      <div class="tag" v-for="(tag, index) in tags" :key="index">
        {{ tag }}
      </div>
    </div>
    <input type="text" v-model="currentValue" @keydown="handleKeyDown" />
  </div>
</template>

<style scoped></style>
