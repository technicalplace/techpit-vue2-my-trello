<template>
  <div class="list">
    <div class="listheader">
      <p class="list-title">{{ title }}</p>
      <p class="list-counter">total:{{ totalCardInList }}</p>
      <div class="deletelist" @click="removeList">×</div>
    </div>
    <draggable>
      <card-view
        v-for="(item, index) in cards"
        :body="item.body"
        :key="item.id"
        :cardIndex="index"
        :listIndex="listIndex"
      />
    </draggable>
    <card-add :list-index="listIndex" />
  </div>
</template>

<script>
import draggable from 'vuedraggable'
import CardAdd from './Card-add.vue'
import CardView from './Card-view.vue'
export default {
  components: {
    CardAdd,
    CardView,
    draggable
  },
  props: {
    title: {
      type: String,
      required: true,
    },
    cards: {
      type: Array,
      require: true,
    },
    listIndex: {
      type: Number,
      required: true,
    }
  },
  computed: {
    totalCardInList() {
      return this.cards.length
    }
  },
  methods: {
    removeList() {
      if (confirm('本当にこのリストを削除しますか？')) {
        this.$store.dispatch('removelist', { listIndex: this.listIndex })
      }
    }
  }
}
</script>