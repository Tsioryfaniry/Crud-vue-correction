<script>
import Drawer from "./components/Drawer.vue";
import UserCard from "./components/UserCard.vue";
import UserDetail from "./components/UserDetail.vue";

export default {
  components: {
    Drawer,
    UserCard,
    UserDetail,
  },
  data() {
    return {
      users: [],
      userDetail: {},
      showDetail: false,
    };
  },
  methods: {
    handleValidate(data) {
      this.users = [...this.users, data];
    },
    handleView(user) {
      this.userDetail = user;
      this.showDetail = true;
      console.log(user);
    },
  },
};
</script>

<template>
  <div>
    <Drawer @validate="handleValidate" />
    <div class="card-wrap">
      <UserCard
        v-for="(u, index) in users"
        :key="`u-${index}`"
        :data="u"
        @view="handleView(u)"
      />
    </div>
    <UserDetail :data="userDetail" :visible="showDetail" @close="showDetail = false" />
  </div>
</template>
