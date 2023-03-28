<script>
export default {
  name: "Button",
  props: {
    label: {
      type: String,
      required: true,
    },
  },
  emits: ["clickBtn"],
  methods: {
    handleClick(e) {
      this.$emit("clickBtn", e);
    },
  },
};
</script>

<template>
  <button type="button" @click="handleClick">
    {{ label }}
  </button>
</template>
