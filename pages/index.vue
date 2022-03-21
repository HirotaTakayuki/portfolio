<template>



  <v-row justify="center">
    <!-- ここから自分の情報に編集してください -->
    <!-- ヘッダー画像 -->
    <v-img src="/header4_img.png" width="70%" height="900" />

    <v-col cols="12" align="center">
      <!-- アイコン画像 -->
      <img
        src="/yourIcon.jpg"
        width="240"
        height="240"
        class="ma-12 rounded-circle"
      />
      <!-- 自己紹介 -->
      <p class="text-h3">「1. 名前」</p>
      <p class="text-h6 text--secondary mb-12">
        「2. 細かい自己紹介」<br />
        例えば、どうしてエンジニアになったのか or なりたいのかなど。<br />
        もし思いつかなければ好きなご飯のおかずを書いてください。
      </p>

      <!-- スキル -->
      <p class="text-h4">スキル</p>
      <p class="text-h6 text--secondary mb-12">「3. 技術スタック」</p>

      <!-- 趣味 -->
      <p class="text-h4">趣味</p>
      <p class="text-h6 text--secondary mb-12">「4. 趣味」</p>

      <!-- 制作物 -->
      <p class="text-h4">制作物</p>
      <v-row class="ma-12">

      <!-- この下からコメントアウト外す：「コードミッション1」 -->
        <v-col cols="4" class="px-12"
          v-for="content in contents.contents" :key="content.id">
          <nuxt-link :to="`/works/${content.id}/`">
            <v-card elevation="2" height="200">
              <v-card-title>{{ content.title }}</v-card-title>
              <v-img :src="content.capture.url" height="240" />
            </v-card>
          </nuxt-link> 
        </v-col>
      <!-- この上までコメントアウト外す -->

      </v-row>

      <!-- モーダル -->
      <v-row class="ma-12">

        <!-- <transition name="modal" appear>
          <div class="modal__overlay">
            <div class="modal__window">
              <div class="modal__content">
                <slot />
              </div>
            </div>
          </div>
        </transition> -->

      </v-row>
    </v-col>

    <div class="button-area">
      <nuxt-link to="/contact/" class="button">お問い合わせ</nuxt-link>
    </div>

    <button @click="on">表示</button>
    <div class="modal" v-bind:class="modal_class">
      <div class="modal-background" @click="on"></div>
        <div class="modal-card">
          <header class="modal-card-head">
            <p class="modal-card-title">Modal title</p>
            <button class="delete" aria-label="close"  @click="on"></button>
          </header>
          <section class="modal-card-body">

          <!-- Content ... -->
          </section>
      
      <footer class="modal-card-foot">
        <button class="button is-success">Save changes</button>
        <button class="button" @click="on">Cancel</button>
      </footer>
      </div>
    </div>
  </v-row>
</template>

<script>


// この下からコメントアウト外す：コードミッション4
export default {
  async asyncData({ $microcms }) {
    const contents = await $microcms.get({
      endpoint: "contents",
    });
    return {
      contents,
    };
  },

    data(){
        return {
          modal_class:""
        }
    },
    methods:{
      on:function(){
        if (this.modal_class == "is-active"){
          this.modal_class = ""
        }else{
          this.modal_class = "is-active"
        }
      }
    }

};
// この上までコメントアウト外す


</script>

<style lang="scss" scoped>
.modal {
  &__overlay {
    display: flex;
    align-items: center;
    justify-content: center;
    position: fixed;
    z-index: 100;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    background: rgba(0, 0, 0, 0.7);
  }

  &__window {
    height: 70%;
    width: 70%;
    overflow: hidden;
    background-color: aquamarine;
  }

  &__content {
    height: 100%;
    padding: 30px;
  }
}

// transition
.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.4s;
  .modal__window {
    transition: opacity 0.4s, transform 0.4s;
  }
}
.modal-leave-active {
  transition: opacity 0.6s ease 0.4s;
}
.modal-enter,
.modal-leave-to {
  opacity: 0;
  .modal__window {
    opacity: 0;
    transform: translateY(-20px);
  }
}
</style>