<template>
<div class="screen">
<div v-if="game.id">
    <div class="opponent">
        <div class="opponent-hand">
            <div v-for="card in game.players[1].hand" @click="setOpponent(card)" :key="card.id">
              <img v-if="!card.visible" src="@/assets/card.jpg" class="hidden">
              <div class="opp-card" v-else-if="card.visible">
                <img :src="card.img">
                <span class="defense">{{card.defense}}</span>
                <span class="attack">{{card.attack}}</span>
                <span class="health">{{card.health}}</span>
            </div>
        </div>
      </div>
        <h1>{{game.players[1].name}}</h1>
    </div>
    <opponent />
    <button @click='fight({ 
      "playerId": game.players[0].id, "opponentId": game.players[1].id, "playerCardId": hero.id, "opponentCardId": opponent.id, gameId: game.id,
    })' 
    v-if="hero.id && opponent.id">FIGHT</button>
    <hero />
    <div class="hero">
        <h1>{{game.players[0].name}}</h1>
        <div class="hero-hand">
            <div class="hero-card" v-for="card in game.players[0].hand" @click="setHero(card)" :key="card.id">
              <span class="defense">{{card.defense}}</span>
              <span class="attack">{{card.attack}}</span>
              <span class="health">{{card.health}}</span>
              <img :src="card.img">
            </div>
        </div>
    </div>
</div>
            <div class="instruct"><h3> DEFENSE <span class="mid">HEALTH</span> ATTACK </h3></div>
</div>
</template>

<script>
import Hero from "@/components/Hero";
import Opponent from "@/components/Opponent";
export default {
  name: "Game",
  data() {
    return {};
  },
  computed: {
    game() {
      return this.$store.state.game;
    },
    hero() {
      return this.$store.state.hero;
    },
    opponent() {
      return this.$store.state.opponent;
    }
  },
  mounted() {
    if (!this.game.id) {
      this.$store.dispatch("getGame", this.$route.params.gameId);
    }
  },
  methods: {
    setHero(card) {
      this.$store.dispatch("setHero", card);
    },
    setOpponent(card) {
      this.$store.dispatch("setOpponent", card);
    },
    fight(payload) {
      this.$store.dispatch("fight", payload);
    },
  },
  components: {
    Hero,
    Opponent
  }
};
</script>

<style scoped>
.screen{
  background-color: red;
  height: 98vh;
}
.instruct{
  position: absolute;
  text-align: center;
  width: 100%;
  bottom: 43.3%;
  font-family: 'Rock Salt'
}
.mid{
 color: white;
}
.opponent h1 {
  position: absolute;
  text-align: center;
  width: 100%;
  font-family: 'Rock Salt';
}
.hero h1 {
  position: absolute;
  text-align: center;
  width: 100%;
  bottom: 30vh;
  font-family: 'Rock Salt';
}
.opponent-hand {
  display: flex;
  justify-content: center;
}
.hero-hand {
  display: flex;
  position: absolute;
  justify-content: center;
  z-index: 1;
  bottom: 0vh;
  width: 100vw;
}
.hidden {
  margin: 10px;
  height: 30vh;
  width: 20vh;
  z-index: 1;
}
.opp-card {
  display: flex;
  position: relative;
  justify-content: center;
  background-color: rgb(0, 0, 0);
  height: 30vh;
  width: 20vh;
  margin: 10px;
  z-index: 1;
}
.hero-card {
  display: flex;
  position: relative;
  justify-content: center;
  background-color: rgb(0, 0, 0);
  height: 30vh;
  width: 20vh;
  margin: 10px;
  z-index: 1;
}
.opp-card img {
  position: absolute;
  height: 25vh;
  width: 15vh;
  bottom: 1vh;
}
.hero-card img {
  position: absolute;
  height: 25vh;
  width: 15vh;
  bottom: 1vh;
}
.defense {
  position: absolute;
  left: 3rem;
  top: 1rem;
  z-index: 2;
  color: red;
}

.attack {
  position: absolute;
  right: 3.5rem;
  top: 1rem;
  z-index: 2; 
  color: red;
}
.health {
  position: absolute;
  top: 1rem;
  z-index: 2;
  color: white;
}
</style>