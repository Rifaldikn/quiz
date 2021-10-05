<template>
  <v-app>
    <v-main>
      <Greetings v-if="screen == 'start'" @clickedToStart="clickToStartBtn" />
      <Quiz v-if="screen == 'quiz'" @goToHome="getToHome" />
    </v-main>
  </v-app>
</template>

<script>
import Greetings from "./components/Greetings";
import Quiz from "./components/Quiz";

export default {
  name: "App",

  components: {
    Greetings,
    Quiz,
  },

  data: () => ({
    screen: "quiz",
  }),
  methods: {
    getToHome() {
      this.screen = "start";
    },
    clickToStartBtn() {
      this.screen = "quiz";
    },
  },
};
</script>
