<template>
  <div>
    <header>
      MY MEMO LIST
    </header>
    <main>
      <p class="info-line">ALL: 0 task</p>
      <list-add />
    </main>
  </div>
</template>

<script>
import ListAdd from './ListAdd.vue'

export default {
  components: { 
    ListAdd 
    },
  
}
</script>