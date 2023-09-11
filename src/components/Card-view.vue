<template>
  <div class="card">
    <button class="close-button" @click="removeCardFromList">
      ✕
    </button>
    <div class="body">
      {{ body }}
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      body: {
        type: String,
        require: true,
      },
      listIndex: {
        type: Number,
        require: true,
      },
      cardIndex: {
        type: Number,
        require: true,
      }
    },
    methods: {
      removeCardFromList() {
        if (confirm('本当にこのカードを削除しますか？')) {
          this.$store.dispatch('removeCardFromList', { cardIndex: this.cardIndex, listIndex: this.listIndex })
        }
      },
    },
  }
</script>
