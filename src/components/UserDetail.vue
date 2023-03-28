<script>
export default {
  name: "UserDetail",
  props: {
    data: {
      type: Object,
      required: true,
    },
    visible: {
      type: Boolean,
      default: false,
    },
  },
  emits: ["close"],
};
</script>

<template>
  <Transition>
    <div class="user-detail" v-if="visible" :class="{ 'visible-user': visible }">
      <span @click="$emit('close')">X</span>
      <div>
        <img src="https://i.pravatar.cc/40" alt="" />
        <h3>{{ data.firstname }} {{ data.lastname }}</h3>
      </div>
    </div>
  </Transition>
</template>

<style lang="scss" scoped>
.user-detail {
  width: 500px;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  overflow: auto;
  box-shadow: -10px 0 10px 10px rgba(0, 0, 0, 0.1);
  transform: translateX(100%);
  transition: transform 0.75s ease;
  &.visible-user {
    transform: none;
  }
  &.v-enter-active,
  &.v-leave-active {
    transition: transform 0.5s ease;
  }

  &.v-enter-active,
  &.v-enter-from {
    transform: translateX(100%);
  }

  &.v-enter-to {
    transform: none;
  }

  &.v-leave-to,
  &.v-leave-active {
    transform: translateX(100%);
  }
}
</style>
