<template>
  <v-card class="mx-auto my-12" max-width="374">
    <div>
      <input type="text" v-model="task" @keyup.enter="creatTask" />
      <v-btn depressed color="primary" class="btn" @click="creatTask">ok</v-btn>
      <div v-for="(item, i) in items" :key="i">
        <div class="todoContent">
          <input
            type="checkbox"
            :value="item"
            ref="email"
            @change="checklist"
            v-bind:style="styleObject"
          />
          <span>{{ item }} </span>
        </div>
      </div>
      <div v-for="(item, i) in selected" :key="i">
        <v-card-text> {{ item }}</v-card-text>
      </div>
    </div>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      items: [],
      task: "",
      selected: [],
      check: "",
      data: "",
      data: {
        styleObject: {
          // text-decoration: overline;
        },
      },
    };
  },
  methods: {
    creatTask() {
      this.items.push(this.task);
      this.task = "";
    },
    checklist() {
      this.task = this.data;
      this.selected.push(this.task);
    },

    focusInput() {
      this.$refs.email.focus();
    },
  },
};
</script>

<style lang="scss" scoped>
input {
  border: 2px solid rgb(45, 14, 95);
  background-color: rgba(95, 197, 223, 0.5);
  height: 32px;
  border-radius: 5px;
  margin-right: 50px;
}
.btn {
  // background-color: chartreuse !important;
  margin-right: 20px;
}
template {
  background-color: rgb(3, 44, 54);
}
.v-application {
  background-color: #00a86b;
}
.todoContent {
  display: flex;

  align-items: center;
}
</style>