<template>
  <div class="list">
    <div class="listheader">
      <p class="list-title">{{ title }}></p>
      <div class="deletelist" @click="removeList">❌</div>
    </div>
  </div>
</template>

<script>
// ★ここから追記
export default {
  props: {
    title: {
      type: String,
      required: true
    },
    listIndex: {
      type: Number,
      required: true
    }
  },
  methods: {
    removeList: function() {
      if(confirm('ほんとにこのリストを削除しますか？')){
        this.$store.dispatch('removelist', {listindex: this.listindex })
      }
    },
  }
}

</script>