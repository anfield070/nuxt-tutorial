<template>
  <v-app>
    <nuxt></nuxt>
    <Dialog />
  </v-app>
</template>

<script>
import Dialog from "/components/Dialog";
export default {
  components: { Dialog }
};
</script>

<style>
html,
.v-application {
  font-family: "Quicksand", sans-serif;
}
.v-toolbar__title {
  text-align: center;
  width: 100%;
  font-weight: bold;
}

.text-primary {
  color: rgb(0, 114, 245);
}
.text-title {
  font-size: 20px;
  font-weight: bold;
}

.text-main {
  font-size: 20px;
}

.w-100 {
  width: 100%;
}

.my-btn {
  font-size: 20px !important;
  text-transform: none !important;
  height: auto !important;
  padding: 12px 0 !important;
}
</style>
