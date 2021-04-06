<template>
  <div class="container">
    <div>
      <input type="text" v-model="city" placeholder="please enter city name" />
      <v-btn depressed color="primary" class="btn" @click="getData">
        show weather
      </v-btn>
      <p>{{ data }}</p>
      <!-- <ul>
        <li>{{ a.location.name }}</li>
        <li>{{ a.location.localtime }}</li>
        <li>{{ a.current.condition.text }}</li>
      </ul> -->
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      city: null,
      data: null,
    };
  },
  methods: {
    getData() {
      if (this.city) {
        this.$axios
          .$get(
            `http://api.weatherapi.com/v1/current.json?key=a782c16718044942ba4190346212803&q=${this.city}&aqi=no`
          )
          .then((res) => {
            console.log(res);
            let a = res;
            this.data =
              a.location.name +
              "-" +
              a.location.localtime +
              "-" +
              a.current.condition.text;
          });
      } else {
        alert("please enter city name first");
      }
    },
  },
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
input {
  border: 2px solid rgb(45, 14, 95);
  background-color: rgba(95, 197, 223, 0.5);
  height: 32px;
  border-radius: 5px;
  justify-content: center;
}
.btn {
  border: 2px solid rgb(45, 14, 95);
  border-radius: 5px;
  margin-right: 10px;
  justify-content: center;
}
</style>
