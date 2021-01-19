<template>
  <div class="list">
    <div class="listheader">
      <p class="list-title">{{ title }}></p>
      <div class="deletelist" @click="removeList">❌</div>
    </div>
    <card-add :listindex="listindex"/>
  </div>
</template>

<script>
import CardAdd from './CardAdd.vue'
// ★ここから追記
export default {
  components: { CardAdd },
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