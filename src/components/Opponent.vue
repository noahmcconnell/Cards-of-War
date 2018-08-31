<template>
 <div class="opponent" v-if="opponent.id">
    <img v-if="!opponent.visible" src="@/assets/card.jpg" class="hidden">
    <div class="opp-card" v-else-if="opponent.visible">
        <img:src="opponent.img">
        <span class="defense">{{opponent.defense}}</span>
        <span class="attack">{{opponent.attack}}</span>
        <span class="health">{{opponent.health}}</span>
    </div>
</div>
</template>

<script>
export default {
  name: "Opponent",
  computed: {
    opponent() {
        return this.$store.state.opponent;
    }
  }
};
</script>

<style scoped>
.opponent {
  position: absolute;
  right: 5rem;
  margin: 10px;
  top: 32vh;
}
.hidden {
  height: 32vh;
  width: 24vh;
  margin: 10px;
  z-index: 1;
}
.opp-card {
  display: flex;
  justify-content: center;
  position: relative;
  height: 30vh;
  width: 20vh;
  margin: 10px;
}
.opp-card img {
  position: absolute;
  height: 30vh;
  width: 20vh;
  bottom: 1%;
}

</style>