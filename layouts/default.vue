<template>
  <v-app>
    <v-app-bar dark color="orange" :clipped-left="clipped" fixed app>
      <v-icon class="mx-2" @click="back">mdi-cloud-outline</v-icon>
      <v-toolbar-title @click="back" v-text="title" />
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container fluid>
        <nuxt />
      </v-container>
    </v-main>
    <p class="footer mt-6">© 2022 XXXXX</p>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      title: "Portfolio",
    };
  },
  methods: {
    back() {
      this.$router.push("/");
    },
  },
};
</script>

<style>
* {
    font-family: "Montserrat","Helvetica Neue",Arial,"Hiragino Kaku Gothic ProN","Hiragino Sans";
  }

.container {
  padding: 0;
}

.footer {
  text-align: center;
}
</style>
