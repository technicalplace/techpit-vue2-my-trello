<template>
  <div>
    <header>
      my Trello
    </header>
    <main>
      <p class="info-line">All:{{ totalCardCount }}tasks</p>
      <div class="list-index">
        <list-card 
          v-for="(item, index) in lists"
          :key="item.id"
          :title="item.title"
          :cards="item.cards"
          :listIndex="index" />
        <list-add />
      </div>
    </main>
  </div>
</template>

<script>
import ListAdd from './list-add.vue'
import ListCard from './List-card.vue'
import { mapState } from 'vuex';

export default {
  components: {
    ListAdd,
    ListCard
  },
  computed: {
    ...mapState([
      'lists'
    ]),
    totalCardCount() {
      return this.$store.getters.totalCardCount
    },
  },
}
</script>