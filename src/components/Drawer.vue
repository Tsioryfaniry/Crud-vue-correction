<script>
import AppButton from "./Button.vue";
export default {
  name: "Drawer",
  components: {
    AppButton,
  },
  data() {
    return {
      formControl: {
        skills: [],
      },
    };
  },
  emits: ["validate"],
  methods: {
    handleAddSkill() {
      this.formControl.skills = [...this.formControl.skills, this.formControl.skill];
      this.formControl.skill = "";
    },
    handleValidate() {
      this.$emit("validate", this.formControl);
      this.formControl = {
        skills: [],
      };
    },
  },
};
</script>

<template>
  <form>
    <div class="form-control">
      <input type="text" v-model="formControl.firstname" placeholder="Firstname" />
    </div>
    <div class="form-control">
      <input type="text" v-model="formControl.skill" placeholder="Skill" />
      <AppButton label="Add" @clickBtn="handleAddSkill" />
      <div v-if="formControl.skills.length > 0">
        <div v-for="(s, index) in formControl.skills" :key="`sk-${index}`">{{ s }}</div>
      </div>
    </div>
    <AppButton label="Validate" @clickBtn="handleValidate" />
  </form>
</template>
