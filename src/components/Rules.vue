<template>
  <div class="container">
    <div class="x">
      <div class="rules">
        <h1>Why is Rock Paper Scissors played?</h1>
        <p>
          This game is played by children and adults and is popular all over the
          world. Apart from being a game played to pass time, the game is
          usually played in situations where something has to be chosen. It is
          similar in that way to other games like flipping the coin, throwing
          dice or drawing straws. There is no room for cheating or for knowing
          what the other person is going to do so the results are usually very
          satisfying with no room for fighting or error.
        </p>
        <h2>What are the rules of RPS?</h2>
        <p>
          Although the game has a lot of complexity to it, the rules to play it
          are pretty simple. The game is played where players deliver hand
          signals that will represent the elements of the game; rock, paper and
          scissors. The outcome of the game is determined by 3 simple rules:
        </p>
        <ul>
          <li>Rock wins against scissors.</li>
          <li>Scissors win against paper.</li>
          <li>Paper wins against rock.</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.container {
  width: 60%;
  height: 100%;
  margin: 0 auto;
  font-family: "Roboto", sans-serif;

  & .rules {
    display: flex;
    flex-flow: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    text-shadow: 1px 1px 10px black;

    & h1 {
      font-size: 2.5rem;
    }

    & h2 {
      font-size: 2rem;
    }

    & p {
      font-size: 1.2rem;
      background: rgba(0, 0, 0, 0.363);
      border-radius: 20px;
      padding: 10px 15px;
      width: 100%;
    }

    & ul {
      margin-top: 0;
      & li {
        font-size: 1rem;
        font-weight: bold;
        margin-top: 5px;
      }
    }
  }
}

@media screen and (max-width: 900px) {
  .container {
    & .rules {
      & h1 {
        font-size: 2rem;
      }

      & h2 {
        font-size: 1.5rem;
      }
    }
  }
}

@media screen and (max-width: 450px) {
  .container {
    width: 95%;

    & .rules {
      & h1,
      h2 {
        font-size: 1.5rem;
        padding: 10px;
      }

      & p {
        font-size: 1.2rem;
        padding: 10px;
      }

      & ul li {
        font-size: 1rem;
      }
    }
  }
}
</style>