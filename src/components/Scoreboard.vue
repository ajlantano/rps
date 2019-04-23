<template lang="html">
<div class="container">
    <div class="content">
  <div class="content__container">
    <p class="content__container__text">
      This Is
    </p>

    <ul class="content__container__list">
      <li class="content__container__list__item">Rock !</li>
      <li class="content__container__list__item">Paper !</li>
      <li class="content__container__list__item">Scissors !</li>
    </ul>
  </div>
</div>
    <hr>
  <div class="row">
      <h3>Player 1</h3>
     <div class="col-2 text-center">{{score.player}}</div>
     <div class="col text-center">
        <button class="btn btn-outline-dark"@click="resetScore">
            <i class="material-icons">refresh</i>
            Reset
        </i>
        </button>
    </div>
    <h3>CPU</h3>
    <div class="col-2 text-center">{{score.cpu}}</div>
  </div>
</div>
</template>

<script>
export default {
    name:'scoreboard',
    props:['score'],
    data(){
        return{}
    },
    methods:{
        resetScore(){
            this.$emit('resetScoreEvent');
        }
    }
}
</script>

<style lang="css" scoped>



</style>
