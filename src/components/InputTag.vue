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
    handleSubmit() {
      if (this.currentValue !== "") {
        const exist = this.tags.some((item) => item === this.currentValue);

        if (!exist) {
          this.tags.push(this.currentValue);
          this.currentValue = "";
        }
      }
    },
    deleteTag(deletedTag) {
      this.tags = this.tags.filter((tag) => tag !== deletedTag);
    },
  },
};
</script>

<template>
  <div class="inputTag">
    <div class="tags">
      <div class="tag" v-for="(tag, index) in tags" :key="index">
        {{ tag }} <button @click="deleteTag(tag)">X</button>
      </div>
    </div>
    <form @submit.prevent="handleSubmit">
      <input type="text" v-model="currentValue" />
    </form>
  </div>
</template>

<style scoped></style>
