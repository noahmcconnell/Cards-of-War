<template>
    <div class="hero" v-if="hero.id">
        <span class="defense">{{hero.defense}}</span>
        <span class="attack">{{hero.attack}}</span>
        <span class="health">{{hero.health}}</span>
        <img :src="hero.img"/>
    </div>
</template>

<script>
export default {
    name: 'Hero',
    computed: {
        hero(){
            return this.$store.state.hero
        }
    }
}
</script>
