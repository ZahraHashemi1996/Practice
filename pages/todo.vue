<template>
  <div class="d-flex flex-column justify-center align-center">
    <div class="w-50 d-flex justify-center align-center">
      <v-text-field
        label="Type to add task"
        type="text"
        v-model="task"
        @keyup.enter="creatTask"
        ref="email"
      ></v-text-field
      ><v-btn elevation="2" color="primary" class="mr-4" @click="creatTask"
        >Add Task</v-btn
      >
    </div>
    <div class="w-50 d-flex align-start flex-column">
      <h4>Uncompleted Tasks</h4>
      <div v-for="(item, i) in items" :key="i">
        <v-checkbox :label="item" @click="doo(item, i)"> </v-checkbox>
      </div>
    </div>
    <div class="w-50 d-flex align-start flex-column">
      <h4>Completed Tasks</h4>
      <div v-for="(item, i) in CompletedTasks" :key="i">
        <v-checkbox :label="item"> </v-checkbox>
      </div>
      <!-- <v-container fluid>
        <p>{{ selected }}</p>
        <v-checkbox v-model="task" :label="item" :value="item"></v-checkbox>
      </v-container> -->
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [],
      task: "",
      check: "",
      checkbox: false,
      CompletedTasks: [],
    };
  },
  mounted() {
    this.$refs.email.focus();
  },
  methods: {
    creatTask() {
      this.items.push(this.task);
      this.task = "";
    },
    doo(item, index) {
      this.CompletedTasks.push(item);
      this.items.splice(index, 1);
    },
  },
};
</script>

<style lang="scss" scoped>
.w-50 {
  width: 50%;
}
.v-input--checkbox {
  margin-top: 0px;
}
</style>
