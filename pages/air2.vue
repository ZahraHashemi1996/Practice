<template>
  <div class="container d-flex justify-center align-center">
    <span class="bg"> </span>
    <div>
      <div class="d-flex align-center">
        <v-text-field
          type="text"
          v-model="city"
          placeholder="please enter city name"
          @keyup.enter="getData"
        ></v-text-field>

        <v-btn rounded color="#05004C" class="mr-4" @click="getData"
          >show weather</v-btn
        >
      </div>

      <v-list-item>{{
        data &&
          data.location &&
          data.location.name + ",&nbsp;" + data.location.country
      }}</v-list-item>
      <v-list-item>{{
        data && data.location && data.location.localtime
      }}</v-list-item>
      <div class="img d-flex">
        <v-list-item>
          {{
            data &&
              data.current &&
              data.current.condition &&
              data.current.condition.text
          }}
        </v-list-item>
      </div>
      <img
        v-if="isDataExist"
        :src="require(`assets/img/weather/${getIconCode()}`)"
        width="64"
        height="64"
      />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      city: "",
      data: ""
    };
  },
  methods: {
    getData() {
      this.$axios
        .$get(
          `http://api.weatherapi.com/v1/current.json?key=a782c16718044942ba4190346212803&q=${this.city}&aqi=no`
        )
        .then(res => {
          this.data = res;
        });
    },
    getIconCode() {
      let code = this.data?.current?.condition?.icon.split("/");
      if (code) {
        return code[6];
      } else {
        return "unknown.png";
      }
    },
    isDataExist() {
      let hasNumber = /\d/;
      return hasNumber.test(this.data?.current?.condition?.icon);
    }
  }
};
</script>

<style lang="scss" scoped>
::v-deep .v-btn__content {
  color: white;
}
.theme--light.v-list-item:not(.v-list-item--active):not(.v-list-item--disabled) {
  color: rgba(33, 3, 102, 0.87) !important;
}
.bg {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  background: url("@/assets/img/weather.jpg") no-repeat center center;
  background-size: cover;
  transform: scale(1.1);
  opacity: 0.5;
}
.img {
  width: 30%;
}
</style>
