<template>
<div class="modal">
  // 背景に全く同じイベントを追加
  <div class="bg" @click="$emit('closeModal')" />
  <div class="modal-wrap">
    <button @click="$emit('closeModal')"> 
      <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><path d="M24 20.188l-8.315-8.209 8.2-8.282-3.697-3.697-8.212 8.318-8.31-8.203-3.666 3.666 8.321 8.24-8.206 8.313 3.666 3.666 8.237-8.318 8.285 8.203z"/></svg>
      <p>ここを押せば閉じる</p>
    </button>
  </div>
</div>
</template>

<style lang="scss" scoped>
.modal {
  position: fixed;
  top: 0;
  width: 100%;
  height: 100%;
  .modal-wrap {
    background-color: rgba(0,0,0,0.5);
    height: 100%;
  }
}
</style>