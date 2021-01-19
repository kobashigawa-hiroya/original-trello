<template>
  <div class="list">
    <div class="listheader">
      <p class="list-title">{{ title }}></p>
      <div class="list-counter">total: {{ totalCardlinst }}</div>
      <div class="deletelist" @click="removeList">❌</div>
    </div>
    <card v-for="(item,index) in cards"
      :body="item.body"
      :key="item.id"
      :cardindex="index"
      :listindex="listindex"
      />

    <card-add :listindex="listindex"/>
  </div>
</template>

<script>
import Card from './Card.vue'
import CardAdd from './CardAdd.vue'

export default {
  components: { CardAdd, Card },
  props: {
    title: {
      type: String,
      required: true
    },
    listIndex: {
      type: Number,
      required: true
    },
    cards: {
      type:String,
      required: true
    },
  },
  computed: {
    totalCardlist() {
      return this.cards.length
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