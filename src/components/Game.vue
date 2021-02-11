<template>
  <div class="game">
    <h1>Rock Paper Scissors</h1>
    <div class="btn-restart" v-if="finished">
      <h3>{{ this.message }}</h3>
      <button @click="restart">Yeniden <i class="fas fa-sync-alt"></i></button>
    </div>
    <div class="scor-table">
      <div id="me" class="user">Me</div>
      <div id="you" class="user">You</div>
      <span id="me-score">{{ meScore }}</span
      >:<span id="you-score">{{ youScore }}</span>
    </div>
    <div class="info" v-if="!finished">
      <h2>{{ result }}</h2>
    </div>
    <div class="image-buttons" v-if="!finished">
      <div id="Rock" class="select" @click="onChoice">
        <img src="../assets/images/rock.jpg" alt="Rock" />
      </div>
      <div id="Paper" class="select" @click="onChoice">
        <img src="../assets/images/paper.jpg" alt="Paper" />
      </div>
      <div id="Scissors" class="select" @click="onChoice">
        <img src="../assets/images/scissors.jpg" alt="Scissors" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      choices: ["Rock", "Paper", "Scissors"],
      meChoise: "",
      youChoise: "",
      meScore: 0,
      youScore: 0,
      result: "",
      finished: false,
      message: "",
    };
  },
  watch: {
    meScore: function () {
      if (this.meScore == 3) {
        this.finished = true;
        this.message = "You Win Dude 🤘";
      }
    },
    youScore: function () {
      if (this.youScore == 3) {
        this.finished = true;
        this.message = " You Lost Dude 😭";
      }
    },
  },
  methods: {
    onChoice(e) {
      this.youChoise = this.choices[
        Math.floor(Math.random() * this.choices.length)
      ];
      this.meChoise = e.currentTarget.id;
      this.game();
    },
    game() {
      switch (this.meChoise + this.youChoise) {
        case "RockScissors":
        case "PaperRock":
        case "ScissorsPaper":
          this.meScore++;
          this.result = this.meChoise + " beats " + this.youChoise;
          break;
        case "RockPaper":
        case "PaperScissors":
        case "ScissorsRock":
          this.youScore++;
          this.result = this.youChoise + " beats " + this.meChoise;
          break;
        case "RockRock":
        case "PaperPaper":
        case "ScissorsScissors":
          this.result = "Draw Dude 😜";
          break;
      }
    },
    restart() {
      Object.assign(this.$data, this.$options.data());
    },
  },
};
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Luckiest+Guy&display=swap");
@mixin user-info {
  position: absolute;
  font-size: 1.5rem;
  width: 70px;
  height: 30px;
  top: 25px;
  letter-spacing: 0;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.game {
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-items: center;
  padding: 20px 50px;

  & h1 {
    text-align: center;
    font-size: 5rem;
    letter-spacing: 10px;
    font-family: "Luckiest Guy", cursive;
    text-shadow: 1px 1px 10px black;
    animation: fadeBottom 1000ms cubic-bezier(0.22, 0.32, 0, 1.54) 400ms;
  }
  & h2 {
    text-align: center;
    font-size: 2rem;
    margin: 100px 0px 50px;
  }

  & .btn-restart {
    display: flex;
    flex-flow: column;
    width: 100%;
    height: auto;
    justify-content: center;
    margin-top: 30px;

    & h3 {
      text-align: center;
      margin-bottom: 20px;
      font-size: 2rem;
      letter-spacing: 5px;
      font-family: "Roboto", sans-serif;
    }

    & button {
      width: 150px;
      height: 35px;
      outline: none;
      border: 0;
      color: white;
      font-size: 18px;
      cursor: pointer;
      margin: auto;
      border-radius: 15px;
      background-color: slateblue;
    }
  }
  /* Score Table */
  & .scor-table {
    border: 3px solid white;
    width: 250px;
    margin: 40px auto;
    color: white;
    letter-spacing: 5px;
    font-size: 46px;
    border-radius: 10px;
    text-align: center;
    padding: 15px 20px;
    font-family: sans-serif;
    position: relative;
    animation: fadeInToRight 1000ms cubic-bezier(0.22, 0.32, 0, 1.54) 400ms;

    & .user {
      padding: 2px 10px;
      background-color: slateblue;
    }

    & #me {
      @include user-info;
      left: -35px;
    }

    & #you {
      @include user-info;
      left: 210px;
    }
  }

  & .info {
    margin-top: -50px;
  }
  /* Image Buttons */

  & .image-buttons {
    animation: fadeInToLeft 1000ms cubic-bezier(0.22, 0.32, 0, 1.54) 400ms;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 50px;

    & .select {
      display: inline-block;
      height: auto;
      border-radius: 100%;

      & img {
        width: 200px;
        height: auto;
        margin: 0 20px;
        border-radius: 100%;
      }

      &:hover {
        cursor: pointer;
        background-color: white;
      }
    }
  }
}
@keyframes fadeInToRight {
  from {
    opacity: 0;
    transform: translateX(+200px);
  }
  to {
    opacity: 1;
    transform: translateX(0px);
  }
}
@keyframes fadeInToLeft {
  from {
    opacity: 0;
    transform: translateX(-200px);
  }
  to {
    opacity: 1;
    transform: translateX(0px);
  }
}
@keyframes fadeBottom {
  from {
    opacity: 0;
    transform: translateY(-400px);
  }
  to {
    opacity: 1;
    transform: translateY(0px);
  }
}

@media screen and (max-width: 450px) {
  @mixin user-info {
    font-size: 1.2rem;
    height: 25px;
    top: 15px;
  }
  .game {
    & h1 {
      font-size: 2rem;
      margin-top: -15px;
    }
    & h2 {
      text-align: center;
      font-size: 1.8rem;
      margin: 100px 0px 50px;
    }

    & .btn-restart {
      margin-top: 20px;
      & h3 {
        font-size: 1.5rem;
      }
    }

    & .scor-table {
      width: 250px;
      font-size: 1.5rem;

      & #me {
        @include user-info;
      }

      & #you {
        @include user-info;
        left: 210px;
      }
    }

    & .info {
      margin-top: -100px;
    }
    /* Image Buttons */

    & .image-buttons {
      bottom: 200px;

      & .select {
        display: inline-block;
        height: auto;
        border-radius: 100%;

        & img {
          width: 100px;
        }

        &:hover {
          background-color: transparent;
        }
      }
    }
  }
}
@media screen and (max-width: 375px) {
  .game {
    & .scor-table {
      width: 150px;
      & #me {
        left: -56px;
      }

      & #you {
        left: 130px;
      }
    }
    & h2 {
      font-size: 1.2rem;
    }
    & .btn-restart h3 {
      font-size: 1rem;
    }
    & .image-buttons {
      bottom: 60px;
      & .select img {
        width: 80px;
      }
    }
  }
}
</style>
