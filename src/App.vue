<template>
    <div id="app">
        <div class="container">
            <scoreboard :score="score" @resetScoreEvent="resetScore" />
            <choices @makeChoiceEvent ="playRound" v-show="!resultWindow.show">

            </choices>
            <result-window :rw="resultWindow" @playAgainEvent = "newRound" v-show="resultWindow.show"/>
        </div>
    </div>
</template>

<script>
import Scoreboard from './components/Scoreboard'
import Choices from './components/Choices'
import ResultWindow from './components/ResultWindow'
export default {
  name: 'app',
  components:{ Scoreboard, Choices, ResultWindow },
  data () {
    return {
        score:{
            player:0,
            cpu:0
        },
        resultWindow:{
            text:'',
            show: false
        }
        }
    },
    methods:{
        resetScore(){
            let reset = confirm('Do you Want to Reset?');
            if(reset){
            this.score = {player: 0, cpu: 0 };
            }
        },
        playRound(playerChoice){
            let cpuChoice = Math.floor(Math.random() * 3);

            if (playerChoice == cpuChoice){
                this.showResult('draw');
            }else if ((playerChoice = cpuChoice + 3) % 3 == 1) {
                this.showResult('win');
            } else {
                this.showResult('lose');
            }
        },
        showResult(result){
            this.resultWindow.show = true;
            switch(result){
                case 'draw':
                this.resultWindow.text = "You got a draw!";
                break;
                case 'win':
                this.resultWindow.text = "WIENER WIENER CHICKEN DINNER";
                this.score.player ++;

                break;
                case 'lose':
                this.resultWindow.text = "LOSER! YOU SUCK";
                this.score.cpu ++;

                break;
            }
        },
        newRound(){
            this.resultWindow.show = false;
        }
    }
}
</script>

<style lang="scss">
#choicebox{
    margin-top: 2rem;
    border: 1px solid black;


}
#app{
    background-color: #6fffe9;
    background-image: linear-gradient(#6fffe9,#3a506b);
    background: #6fffe9;
    background: linear-gradient(#6fffe9,#3a506b);
    height:100vh;


}
#playAgain {
  height: 250px;
  width: 250px;
  margin: 0 auto;
  background-color: red;
  animation-name: stretch;
  animation-duration: 1.5s;
  animation-timing-function: ease-out;
  animation-delay: 0;
  animation-direction: alternate;
  animation-iteration-count: infinite;
  animation-fill-mode: none;
  animation-play-state: running;
}

@keyframes stretch {
  0% {
    transform: scale(.3);
    background-color: red;
    border-radius: 100%;
  }
  50% {
    background-color: #6fffe9;
  }
  100% {
    transform: scale(1.5);
    background-color: #3a506b;
  }
}
.content {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  height: 160px;
  overflow:hidden;

  font-family: 'Lato', sans-serif;
  font-size: 35px;
  line-height: 40px;
  color: #ecf0f1;

  &__container {
    font-weight: 600;
    overflow: hidden;
    height: 40px;
    padding: 0 40px;

    &:before {
      content: '[';
      left: 0;
    }

    &:after {
      content: ']';
      position: absolute;
      right: 0;
    }

    &:after, &:before {
      position: absolute;
      top: 0;

      color: #16a085;
      font-size: 42px;
      line-height: 40px;

      -webkit-animation-name: opacity;
      -webkit-animation-duration: 2s;
      -webkit-animation-iteration-count: infinite;
      animation-name: opacity;
      animation-duration: 2s;
      animation-iteration-count: infinite;
    }

    &__text {
      display: inline;
      float: left;
      margin: 0;
    }

    &__list {
      margin-top: 0;
      padding-left: 110px;
      text-align: left;
      list-style: none;

      -webkit-animation-name: change;
      -webkit-animation-duration: 10s;
      -webkit-animation-iteration-count: infinite;
      animation-name: change;
      animation-duration: 10s;
      animation-iteration-count: infinite;

      &__item {
        line-height:40px;
        margin:0;
      }
    }
  }
}

@-webkit-keyframes opacity {
  0%, 100% {opacity:0;}
  50% {opacity:1;}
}

@-webkit-keyframes change {
  0%, 12.66%, 100% {transform:translate3d(0,0,0);}
  16.66%, 29.32% {transform:translate3d(0,-25%,0);}
  33.32%,45.98% {transform:translate3d(0,-50%,0);}
  49.98%,62.64% {transform:translate3d(0,-75%,0);}
  66.64%,79.3% {transform:translate3d(0,-50%,0);}
  83.3%,95.96% {transform:translate3d(0,-25%,0);}
}

@-o-keyframes opacity {
  0%, 100% {opacity:0;}
  50% {opacity:1;}
}

@-o-keyframes change {
  0%, 12.66%, 100% {transform:translate3d(0,0,0);}
  16.66%, 29.32% {transform:translate3d(0,-25%,0);}
  33.32%,45.98% {transform:translate3d(0,-50%,0);}
  49.98%,62.64% {transform:translate3d(0,-75%,0);}
  66.64%,79.3% {transform:translate3d(0,-50%,0);}
  83.3%,95.96% {transform:translate3d(0,-25%,0);}
}

@-moz-keyframes opacity {
  0%, 100% {opacity:0;}
  50% {opacity:1;}
}

@-moz-keyframes change {
  0%, 12.66%, 100% {transform:translate3d(0,0,0);}
  16.66%, 29.32% {transform:translate3d(0,-25%,0);}
  33.32%,45.98% {transform:translate3d(0,-50%,0);}
  49.98%,62.64% {transform:translate3d(0,-75%,0);}
  66.64%,79.3% {transform:translate3d(0,-50%,0);}
  83.3%,95.96% {transform:translate3d(0,-25%,0);}
}

@keyframes opacity {
  0%, 100% {opacity:0;}
  50% {opacity:1;}
}

@keyframes change {
  0%, 12.66%, 100% {transform:translate3d(0,0,0);}
  16.66%, 29.32% {transform:translate3d(0,-25%,0);}
  33.32%,45.98% {transform:translate3d(0,-50%,0);}
  49.98%,62.64% {transform:translate3d(0,-75%,0);}
  66.64%,79.3% {transform:translate3d(0,-50%,0);}
  83.3%,95.96% {transform:translate3d(0,-25%,0);}
}


</style>
