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
        experiences: [],
        experience: {},
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
        experiences: [],
        experience: {},
      };
    },
    handleAddExperience() {
      this.formControl.experiences = [
        ...this.formControl.experiences,
        this.formControl.experience,
      ];
      console.log(this.formControl.experiences);
      this.formControl.experience = {};
    },
    /* handleDeleteSkill(deleteIndex) {
      this.formControl.skills = this.formControl.skills.filter(
        (_, index) => index !== deleteIndex
      );
    },
    handleDeleteExp(deleteIndex) {
      this.formControl.experiences = this.formControl.experiences.filter(
        (_, index) => index !== deleteIndex
      );
    }, */
    handleDeleteItemFromList(key, deleteIndex) {
      this.formControl[key] = this.formControl[key].filter(
        (_, index) => index !== deleteIndex
      );
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
      <input type="text" v-model="formControl.lastname" placeholder="Lastname" />
    </div>
    <div class="form-control">
      <input type="number" v-model="formControl.age" placeholder="age" />
    </div>
    <div class="form-control">
      <input type="text" v-model="formControl.role" placeholder="role" />
    </div>
    <div class="form-control">
      <input type="text" v-model="formControl.skill" placeholder="Skill" />
      <AppButton label="Add" @clickBtn="handleAddSkill" />
      <div v-if="formControl.skills.length > 0">
        <div v-for="(s, index) in formControl.skills" :key="`sk-${index}`">
          {{ s }} <span @click="handleDeleteItemFromList('skills', index)">x</span>
        </div>
      </div>
    </div>
    <div class="form-control">
      <input
        type="text"
        v-model="formControl.experience.title"
        placeholder="Experience title"
      />
      <textarea
        type="text"
        v-model="formControl.experience.description"
        placeholder="Experience description"
      ></textarea>
      <input
        type="date"
        v-model="formControl.experience.startDate"
        placeholder="Experience year"
      />
      <input
        type="date"
        v-model="formControl.experience.endDate"
        placeholder="Experience year"
      />

      <AppButton label="Add" @clickBtn="handleAddExperience" />
      <div v-if="formControl.experiences.length > 0">
        <div v-for="(ex, index) in formControl.experiences" :key="`sk-${index}`">
          {{ ex.title }} - {{ ex.startDate }} à {{ ex.endDate }}
          <span @click="handleDeleteItemFromList('experiences', index)">x</span>
        </div>
      </div>
    </div>
    <AppButton label="Validate" @clickBtn="handleValidate" />
  </form>
</template>
