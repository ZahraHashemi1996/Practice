<template>
  <div>
    <v-card
      class="mx-auto my-12"
      max-width="374"
      v-for="(item, i) in items"
      :key="i"
      :info="item"
    >
      <v-img height="250" :src="item.product.src"></v-img>

      <v-card-title> {{ item.product.product_name }}</v-card-title>

      <v-card-actions>
        <v-btn nuxt-to="/" color="primary"> ادامه مطلب </v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>

   

<script>
export default {
  data() {
    return {
      items: [],
    };
  },
  async mounted() {
    let respons = await this.$axios.get(
      "https://www.mobit.ir/api/web/v6/promotion/index?expand=product,product.src"
    );
    this.items = respons.data.items;
  },
};
</script>

<style lang="scss" scoped>
</style>