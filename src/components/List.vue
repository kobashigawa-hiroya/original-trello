<template>
  <div class="list">
    <div class="listheader">
      <p class="list-title">{{ title }}</p>
      <p class="list-counter">total: {{ totalCardInList }}</p>
      <div class="deletelist" @click="removeList">×</div>
     <!-- クリックイベント時にremoveListメソッドをハンドル -->
    </div>
    <draggable group="cards"
               :list="cards"
               @end="$emit('change')">
      <Card v-for="(item, index) in cards"
            :body="item.body"
            :key="item.id"
            :cardIndex="index"
            :listIndex="listIndex"
      />
      <CardAdd :listIndex="listIndex" />
    </draggable>
  </div>
</template>
<script>
import draggable from 'vuedraggable'
import CardAdd from './CardAdd'
import Card from './Card'
export default {
  components: {
    CardAdd,
    Card,
    draggable
  },
  //props受け取る方を指定
  props: {
    title: {
      type: String,
      //String型で受け取る
      required: true
      //必ず受け取る事
    },
    listIndex: {
      type: Number,
      required: true
    },
    cards: {
      type: Array,
      required: true
    },
  },
  computed: {
    totalCardInList() {
      return this.cards.length
    }
  },
  methods: {
    removeList: function() {
      if(confirm('本当にこのリストを削除しますか？')){
        this.$store.dispatch('removelist', { listIndex: this.listIndex })
      }
    },
  }
}
</script>