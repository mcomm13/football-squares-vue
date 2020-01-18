<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">Football Squares Number Picker</div>
      <v-spacer></v-spacer>
      <v-btn href="https://github.com/mcomm13/football-squares-vue" target="_blank" text>
        <span class="mr-2">View on GitHub</span>
        <v-icon>mdi-github-circle</v-icon>
      </v-btn>
    </v-app-bar>

    <v-content>
      <FootballSquares
        v-bind:numberPairs="numberPairs"
        v-on:assign-numbers="numberPairs = assignNumberPairs()"
      />
    </v-content>
    <v-footer>
      <div>&copy; 2019 Michael Commendatore</div>
    </v-footer>
  </v-app>
</template>

<script>
import FootballSquares from "./components/FootballSquares";

export default {
  name: "App",

  components: {
    FootballSquares
  },

  data: () => {
    return {
      numberPairs: [
        { team1: "X", team2: "X" },
        { team1: "X", team2: "X" },
        { team1: "X", team2: "X" },
        { team1: "X", team2: "X" },
        { team1: "X", team2: "X" },
        { team1: "X", team2: "X" },
        { team1: "X", team2: "X" },
        { team1: "X", team2: "X" },
        { team1: "X", team2: "X" },
        { team1: "X", team2: "X" }
      ]
    };
  },
  methods: {
    assignNumberPairs: () => {
      const team1Numbers = getRandomNumbers();
      const team2Numbers = getRandomNumbers();
      let returnValue = [];

      for (let i = 0; i <= 9; i++) {
        returnValue[i] = {
          team1: team1Numbers[i],
          team2: team2Numbers[i]
        };
      }
      return returnValue;
    }
  }
};

const getRandomNumbers = () => {
  const numberPool = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
  const randomizedNumbers = [];
  let randomIndex, randomNumber;

  for (let i = 0; i <= 9; i++) {
    randomIndex = Math.floor(Math.random() * (10 - i));
    randomNumber = numberPool[randomIndex];

    randomizedNumbers.push(randomNumber);
    numberPool.splice(randomIndex, 1);
  }

  return randomizedNumbers;
};
</script>

<style lang="scss">
.v-application--wrap {
  min-height: 75vh;
}
</style>
