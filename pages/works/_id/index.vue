<template>
  <v-row justify="center" align-content="center" class="mx-16">
    <v-col cols="12" align="center">
      <v-spacer class="my-16" />

      <!-- ここからコメントアウト外す -->
      <v-row>
        <v-col cols="6" align="right">
          <v-img contain height="300" :src="content.capture.url" />
        </v-col>

        <v-col cols="6" align="left" class="my-8">
          <p class="text-h3 mb-8">{{ content.title }}</p>
          <p class="text-h6 text--primary">{{ content.overview }}</p>
        </v-col>
      </v-row>
      <!-- ここまでコメントアウト外す -->


      <v-spacer class="my-16" />

      <!-- 概要 -->
      <p class="text-h5">URL</p>
      <a :href="content.url">
        <p class="text-h6 text--secondary mb-12">{{ content.url }}</p>
      </a>

      <!-- 使用技術 -->
      <p class="text-h5">使用技術</p>
      <p class="text-h6 text--secondary mb-12">{{ content.tech }}</p>

      <!-- 果たした役割 -->
      <p class="text-h5">果たした役割</p>
      <p class="text-h6 text--secondary mb-12">{{ content.role }}</p>
    </v-col>

    <p class="button-area">
      <nuxt-link to="/">back</nuxt-link>
    </p>
  </v-row>
</template>

<script>

// この下からコメントアウト外す：「コードミッション4」
 export default {
   async asyncData({ $microcms, params }) {
     const content = await $microcms.get({
       endpoint: `contents/${params.id}`,
     });
     return {
       content,
     };
   },
 };
// この上までコメントアウト外す
</script>
