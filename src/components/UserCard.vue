<script>
export default {
  name: "UserCard",
  props: {
    data: {
      type: Object,
      required: true,
    },
  },
  emits: ["view"],
  methods: {
    handleUserClick() {
      this.$emit("view");
    },
  },
};
</script>

<template>
  <div class="user-card" @click="handleUserClick">
    <h2>{{ data.firstname }}</h2>
    <span>{{ data.skills.join(" ") }}</span>
  </div>
</template>
