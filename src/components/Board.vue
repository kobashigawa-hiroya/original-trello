<template>
  <div>
    <header>
      MY MEMO LIST
    </header>
    <main>
      <p class="info-line">ALL: 0 task</p>
      <div class="list-index">
<list v-for="(item, index) in lists"
      :key="item.id"
      :title="item.title"
      :listIndex="index"
/>      <list-add/>
      </div>
    </main>
  </div>
</template>

<script>
import ListAdd from './ListAdd.vue'
import List from './List'
import { mapState } from 'vuex'

export default {
  components: { 
    ListAdd,
    List,
    },
    computed: {
      ...mapState([
        'lists'
      ]),
    },
  
}
</script>