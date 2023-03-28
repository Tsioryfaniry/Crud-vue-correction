<script>
export default {
  name: "UserDetail",
  props: {
    data: {
      type: Object,
      required: true,
    },
  },
};
</script>

<template>
  <div class="user-detail">
    {{ data.firstname }}
  </div>
</template>
