<template>
  <v-app id="football-squares">
    <!-- <v-content> -->
    <v-container>
      <v-row align="center" justify="center">
        <h1>Use this app to pick random numbers for the headers of your Football Squares grid</h1>
        <v-col cols="12" sm="8" md="4">
          <v-card class="elevation-12">
            <v-card-text>
              <v-row>
                <v-col class="team1-heading">Team 1</v-col>
                <v-col class="team2-heading">Team 2</v-col>
              </v-row>
              <v-row v-for="(pair,index) in numberPairs" :key="index">
                <v-col class="team1-numbers">{{pair.team1}}</v-col>
                <v-col class="team2-numbers">{{pair.team2}}</v-col>
              </v-row>
            </v-card-text>
            <v-card-actions>
              <v-row align="center" justify="center">
                <v-btn v-on:click="$emit('assign-numbers')" color="primary">Get Numbers</v-btn>
              </v-row>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
    <!-- </v-content> -->
  </v-app>
</template>

<script>
export default {
  props: {
    numberPairs: Array
  }
};
</script>

<style lang="scss">
$team1-color: #d62027;
$team2-color: #013369;

h1 {
  text-align: center;
  font-size: 24px;
}

.row {
  text-align: center;
}

.team1-heading {
  color: $team1-color;
  font-size: 18px;
}

.team2-heading {
  color: $team2-color;
  font-size: 18px;
}

.team1-numbers {
  background-color: $team1-color;
  color: #ffffff;
  font-size: 18px;
  border-right: 1px solid #ffffff;
  padding: 6px !important;
}

.team2-numbers {
  background-color: $team2-color;
  color: #ffffff;
  font-size: 18px;
  padding: 6px !important;
}
</style>