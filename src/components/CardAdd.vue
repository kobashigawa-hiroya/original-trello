<template>
  <form :class="classList" @submit.prevent="addCardToList">
    <!-- サブイベント時に addCardToListメソッドをハンドリング-->
    <input v-model="body"
           type="text"
           class="text-input"
           placeholder="新しいメモを追加する"
           @focusin="startEditing"
           @focusout="finishEditing"
    />
    <!-- v-modelにbodyを定義し、dataプロパティとバインド-->
    <button type="submit"
            class="add-button"
            v-if="isEditing || bodyExists">
      Add
    </button>
  </form>
</template>
<script>
export default {
  props: {
    listIndex: {
      type: Number,
      required: true,
    }
  },
  data: function() {
    return {
      body: '',
//addCardToListメソッドを定義し、呼び出し
      isEditing: false,
    }
  },
  computed: {
    classList() {
      const classList = ['addcard']
      if (this.isEditing) {
        classList.push('active')
      }
      if (this.bodyExists) {
        classList.push('addable')
      }
      return classList
    },
    bodyExists() {
      return this.body.length > 0
    }
  },
  methods: {
    startEditing: function() {
      this.isEditing = true
    },
    finishEditing: function() {
      this.isEditing = false
    },
    addCardToList: function() {
      this.$store.dispatch('addCardToList', { body: this.body, listIndex: this.listIndex })
      this.body = ''
    }
  }
}
</script>
