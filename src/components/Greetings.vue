<template>
  <v-container fill-height>
    <v-row class="text-center d-flex align-center">
      <v-col cols="12">
        <div class="display-1">Hello, Welcome</div>
        <div class="headline">
          Simple Quiz made with <span class="green--text">Vuejs</span>
        </div>
      </v-col>
      <v-col>
        <v-btn color="primary" @click="startQuiz">Start Quiz</v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Greetings",

  methods: {
    startQuiz() {
      this.$emit("clickedToStart", "quiz");
    },
  },
};
</script>
