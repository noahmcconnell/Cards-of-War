<template>
 <div class="body">
  <div class="top">
    <h1 class="title">Cards of War</h1>  
  </div>
  <div class="card-set-selection">
    <h1 class="title">SELECT YOUR WARRIORS </h1>
    <div class="sets">
      <div @click="selectDeck(1)" class="set1 set">
      <img src="https://robohash.org/YOUR-TEXT.png?set=set1">
      </div>
      <div @click="selectDeck(2)" class="set2 set"> 
      <img src="https://robohash.org/YOUR-TEXT.png?set=set2">
      </div>
      <div @click="selectDeck(3)" class="set3 set"> 
      <img src="https://robohash.org/YOUR-TEXT.png?set=set3">
      </div>
      <div @click="selectDeck(4)" class="set4 set">
      <img src="https://robohash.org/YOUR-TEXT.png?set=set4">
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: "DeckSelect",
  data() {
    return {};
  },
  methods: {
    selectDeck(deckNum) {
      this.$store.dispatch("selectDeck", deckNum);
    }
  }
};
</script>

<style scoped>
.body{
  background-color: black;
  height: 98vh;
}
.title{
  color: red;
  font-family: 'Rock Salt';
}
.top {
  display: flex;
  justify-content: center;
  font-family: 'Rock Salt';
  font-size: 2.5rem;
}
.card-set-selection {
  position: relative;
  text-align: center;
}
.sets {
  display: flex;
}
.set {
  display: flex;
  justify-content: center;
  height: 35vh;
  width: 35vw;
  margin-top: 3.3rem;
}
.set:hover img {
  background-color: rgba(255, 0, 0, 0.87);
}

</style>