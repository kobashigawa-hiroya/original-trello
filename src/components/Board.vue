<template>
  <div>
    <header>
      クラス週案 早見表
    </header>
    <main>
      <p class="info-line">全部で: {{ totalCardCount }} </p>
           <!-- class="list-index" → draggable class="list-indexに修正"でこれでドラッグ&ドロップはできる -->

      <draggable :list="lists"
            @end="movingList"
            class="list-index">
        <list v-for="(item, index) in lists"
              :key="item.id"
              :title="item.title"
              :cards="item.cards"
              :listIndex="index"
              @change="movingCard"
        />
           <!-- ↑これでドラッグ&ドロップされるたびにデータ更新 -->
  <!-- endイベントを発火し、movingCardメソッドを発火！ -->

        <list-add/>
      </draggable>
    </main>
  </div>
</template>

<script>
import draggable from 'vuedraggable'
import List from './List'
import ListAdd from './ListAdd'
import { mapState } from 'vuex'

export default {
  components: {
    ListAdd,
    List,
    draggable
  },
  computed: {
    ...mapState([
//スプレット演算子でcomputedのローカルのオブジェクトと一緒に定義できる
      'lists'
    ]),
    totalCardCount() {
      return this.$store.getters.totalCardCount
    }
  },
  methods: {
    movingCard: function() {
      this.$store.dispatch('updateList', { lists: this.lists })
    },
    movingList: function() {
      this.$store.dispatch('updateList', { lists: this.lists })
//リストを並び替えた時イベントが発火し、ストアのupdateListメソッドを呼び出す
    }
  }
}
</script>