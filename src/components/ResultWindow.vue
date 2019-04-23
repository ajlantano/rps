<template lang="html">
  <div class="card"id="playAgain">
      <div class="card-body text-center">
          <h3 class="card-title text-center" >{{ rw.text }}</h3>
          <button class="btn btn-outline-dark btn-sx" @click="playAgain">Play Again?</button>
      </div>

  </div>
</template>

<script>
export default {
    name: 'ResultWindow',
    props: ['rw'],
    data(){
        return {}
    },
    methods: {
        playAgain(){
            this.$emit('playAgainEvent');
        }
    }
}
</script>

<style lang="css" scoped>
</style>
