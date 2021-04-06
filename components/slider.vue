<template>
  <div>
    <v-carousel v-model="model" height="400">
      <v-carousel-item v-for="(item, i) in items" :key="i">
        <v-sheet height="100%" tile>
          <v-row class="fill-height" align="center" justify="center">
            <!-- <div class="display-3">Slide {{ i + 1 }}</div> -->
            <img :src="item.download_url" width="100%" height="100%" />
          </v-row>
        </v-sheet>
      </v-carousel-item>
    </v-carousel>
  </div>
</template>

<script>
export default {
  data() {
    return {
      model: 0,
      items: [],
    };
  },
  async mounted() {
    let response = await this.$axios.get(
      "https://picsum.photos/v2/list?limit=5"
    );
    this.items = response.data;
  },
};
</script>

<style lang="scss" scoped>
.slider-main {
  height: 400px;
}
</style>