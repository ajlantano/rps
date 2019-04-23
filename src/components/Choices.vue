<template lang="html">
  <div class="card" id="choicebox">
      <div class="card-body">
          <div class="row">
              <div class="col text-center" v-for="(option,index) in options"id="choices">
                  <button class="btn btn-outline-dark"@click="makeChoice(index)">
                      {{option}}
                  </button>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name:'choices',
    data(){
        return{
            options:['rock', 'paper', 'scissors']
        }
    },
    methods:{
     makeChoice(i) {
        this.$emit('makeChoiceEvent', i);
        }
    }
}
</script>

<style lang="css" scoped>
#choicebox{
    background-color: #6fffe9;
    background-image: linear-gradient(#6fffe9,#3a506b);
    background: #6fffe9;
    background: linear-gradient(#6fffe9,#3a506b);

}

</style>
