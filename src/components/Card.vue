<template>
  <div class="card">
    <button class="close-button" @click="removeCardFromList">
      ×
    </button>
      <!-- clickイベント時にemoveCardFromListメソッドをハンドル -->

    <div class="body">
      {{ body }}
  <!-- マスタッシュ構文でデータバインド -->

    </div>
  </div>
</template>
<script>
export default {
  props: {
    body: {
      type: String,
      required: true
    },
    listIndex: {
      type: Number,
      required: true
    },
    cardIndex: {
      type: Number,
      required: true
    }
  },
  methods: {
    removeCardFromList() {
      if(confirm('ホンマに消します？')) {
        this.$store.dispatch('removeCardFromList', { cardIndex: this.cardIndex, listIndex: this.listIndex })
//click時にremoveCardFromListをハンドル！
      }
    }
  },
}
</script>