<template>
  <v-container>
    <router-view></router-view>
  </v-container>
</template>
<script>
// import AppBarBlurAuth from "@/components/AppBarBlurAuth";
import { FadeTransition } from "vue2-transitions";

export default {
  name: "page-layout",
  components: {
    // AppBarBlurAuth,
    FadeTransition,
  },
  data() {
    return {};
  },
};
</script>