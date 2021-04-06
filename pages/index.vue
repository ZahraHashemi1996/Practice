<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="12" md="12">
      <slider />
      <mainArticle />
    </v-col>
  </v-row>
</template>

<script>
import Logo from "~/components/Logo.vue";
import VuetifyLogo from "~/components/VuetifyLogo.vue";

export default {
  components: {
    Logo,
    VuetifyLogo,
  },
};
</script>
