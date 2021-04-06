<template>
  <div>
    <div class="container">
      <div>
        <input
          type="text"
          v-model="city"
          placeholder="please enter city name"
        />
        <button @click="getData">show weather</button>
        <p>{{ data }}</p>
        <!-- <ul>
          <li>{{ data.location.name }}</li>
          <li>{{ data.location.localtime }}</li>
          <li>{{ data.current.condition.text }}</li>
        </ul> -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      city: "",
      data: "",
    };
  },
  methods: {
    async getData(city) {
      this.$axios.$get(
        `http://api.weatherapi.com/v1/current.json?key=a782c16718044942ba4190346212803&q=${city}&aqi=no`
      );
      //       .then((res) => {
      //         console.log(res);
      //         let a = res;
      //   this.data =
      //     a.location.name +
      //     "-" +
      //     a.location.localtime +
      //     "-" +
      //     a.current.condition.text;
      // },
    },
  },
};
</script>

<style lang="scss" scoped>
</style>