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
    <img src="https://i.pravatar.cc/40" :alt="data.firstname" />
    <h2>{{ data.firstname }}</h2>
    <span>{{ data.skills.join(" ") }}</span>
  </div>
</template>
