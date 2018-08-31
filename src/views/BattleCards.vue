<template>
<deck-select />
</template>
<script>
import DeckSelect from '@/components/DeckSelect'
export default {
  name: "battleCards",
  computed: {
    activeGame(){
      return this.$store.state.game
    }
  },
  components: {
    DeckSelect
  },
  methods: {
  }
};
</script>
