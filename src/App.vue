<template>
  <v-app>
    <v-app-bar app color="amber darken-3" dark>
      <div class="d-flex align-center">
        <v-img
          alt="household-budget-golden-ratio-simulator Logo"
          class="shrink mr-2 hidden-sm-and-down"
          contain
          src="./assets/logo.png"
          transition="scale-transition"
          width="40"
        />
        <v-toolbar-title class="text-sm-h5 text-md-h4 text-subtitle-1 font-navigation">
          家計 黄金比率シミュレーター
        </v-toolbar-title>
        <RatioDescription />
      </div>
    </v-app-bar>

    <v-main>
      <Top />
    </v-main>
  </v-app>
</template>

<style scoped>
.font-navigation {
  font-family: 游ゴシック, "Yu Gothic", メイリオ, Meiryo, Verdana, Helvetica,
    Arial, sans-serif !important;
}
</style>

<script>
import Top from "./components/Top";
import RatioDescription from "./components/RatioDescription.vue"

export default {
  name: "App",

  components: {
    Top,
    RatioDescription
  },
};
</script>