<template>
  <vcontainer>
    <v-btn color="error" class="ma-10" @click="goToHome">
      <v-icon>mdi-chevron-left</v-icon>
      Back
    </v-btn>
    <v-row class=" pa-10">
      <v-col cols="12" class="d-flex justify-center">
        <v-card max-width="750px" width="70%">
          <v-row class="d-flex align-center">
            <v-col>
              <v-card-title primary-title>
                Your Score : {{ score }}
              </v-card-title>
            </v-col>
            <v-col class="d-flex justify-end mx-5">
              <v-btn color="primary" @click="resetScore">Try Again</v-btn>
            </v-col>
          </v-row>
        </v-card>
      </v-col>
      <v-col cols="12" class="d-flex justify-center">
        <v-card max-width="750px" width="70%" class="pa-5">
          <v-row no-gutters>
            <v-col cols="12" v-for="(item, index) in questions" :key="index">
              <v-card-title primary-title> Soal {{ index + 1 }} </v-card-title>
              <v-card-text class="body-2">
                {{ item.text }}
              </v-card-text>
              <v-radio-group v-model="answers[`${index}`]" class="px-5">
                <v-radio
                  v-for="(option, index) in item.options"
                  :key="index"
                  :label="option"
                  :value="index"
                ></v-radio>
              </v-radio-group>
              <v-divider
                v-if="questions.length == questions.length - 1"
              ></v-divider>
            </v-col>
            <v-col class="d-flex justify-end">
              <v-btn color="primary" @click="getScore">Finish</v-btn>
            </v-col>
          </v-row>
        </v-card>
      </v-col>
    </v-row>
  </vcontainer>
</template>

<script>
export default {
  methods: {
    goToHome() {
      this.$emit("goToHome", "start");
    },
    resetScore() {
      this.score = 0;
      this.answers = [];
    },
    getScore() {
      let score = [];
      this.answers.forEach((element, index) => {
        let correctAnswer = this.questions[index];
        console.log(correctAnswer);
        if (element == correctAnswer.answer) {
          score.push(true);
        } else {
          score.push(false);
        }
      });

      score =
        (score.filter((x) => x == true).length / this.questions.length) * 100;
      this.score = score.toPrecision(3);
    },
  },
  data() {
    return {
      answers: [],
      score: 0,
      questions: [
        {
          text:
            "Penghubung antar tulang yang satu dengan tulang lainnya yang menyebabkan tulang dapat digerakkan disebut",
          answer: 1,
          options: ["A. Kulit", "B. Sendi", "C. Tulang", "D. Otot"],
        },
        {
          text:
            "Sendi yang ada di antara tulang telapak tangan dan juga pada pangkal ibu jari, adalah jenis sendi",
          answer: 1,
          options: ["A. Peluru", "B. Pelana", "C. Engsel", "D. Geser"],
        },
        {
          text:
            "Bagian-bagian mata yang bertugas untuk menyerap cahaya yang datang adalah",
          answer: 3,
          options: ["A. Kelopak", "B. Iris", "C. Selaput Bening", "D. Retina"],
        },
      ],
    };
  },
};
</script>
