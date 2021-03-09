<template>
  <form :class="classList" @submit.prevent="addList">
    <input v-model="title"
           type="text"
           class="text-input"
           placeholder="クラスを追加する"
           @focusin="startEditing"
           @focusout="finishEditing"
    >
    <!-- イベントハンドラ①focusin="startEditing"フォーカスされる ②@focusout="finishEditing"フォーカス外す -->
    <button type="submit"
            class="add-button"
            v-if="isEditing || titleExists">
  <!--  v-ifでフォーカスされている時、入力されている時titleExistsを指定したのでどちらかがtrueになるとボタンが表示-->
      追加する！
    </button>
  </form>
</template>
<script>
export default {
  data: function() {
    return {
      title: '',
      isEditing: false,
    }
  },
  computed: {
    classList() {
      const classList = ['addlist']
      if (this.isEditing) {
        classList.push('active')
      }
      if (this.titleExists) {
        classList.push('addable')
      }
      return classList
    },
    titleExists() {
      return this.title.length > 0
    },
  },
  methods: {
    addList: function() {
      this.$store.dispatch('addlist', { title: this.title })
      this.title = ''
    },
    startEditing() {
      this.isEditing = true
      //フォーカスされている時にスタイルを当てる
    },
    finishEditing() {
      this.isEditing = false
    },
  }
}
</script>
