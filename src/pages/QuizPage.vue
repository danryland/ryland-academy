<template>
  <q-page class="page-quiz">
    <h1>{{ activeQuestionItem.text }}</h1>
    <q-list :class="{ 'show-answer': showAnswer === true }">
      <template
        v-for="(option, index) in activeQuestionItem.options"
        :key="option"
      >
        <q-item
          clickable
          tag="label"
          :class="{
            'active-item': answers[activeQuestionIndex] === index,
            'answer-correct':
              isAnswerCorrect === true &&
              answers[activeQuestionIndex] === index,
            'answer-wrong':
              isAnswerCorrect === false &&
              answers[activeQuestionIndex] === index,
          }"
        >
          <q-item-section>
            <q-radio
              :disable="showAnswer"
              :label="option"
              color="yellow"
              v-model="answers[activeQuestionIndex]"
              :val="index"
            />
          </q-item-section>
        </q-item>
      </template>
    </q-list>
    <q-btn
      v-if="answers[activeQuestionIndex] != null && !showAnswer"
      class="btn-large full-width"
      color="primary"
      rounded
      no-caps
      label="Check"
      @click="checkAnswer()"
    />
    <q-btn
      v-if="answers[activeQuestionIndex] != null && showAnswer"
      class="btn-large full-width"
      color="green"
      rounded
      no-caps
      label="Next"
      @click="nextQuestion()"
    />
  </q-page>
  <q-footer class="footer-quiz">
    <q-btn
      class="btn-large full-width"
      flat
      rounded
      no-caps
      label="Learn factors"
      :to="{ name: 'learn' }"
    />
  </q-footer>
</template>

<script lang="ts">
import { ref, computed, Ref } from 'vue';

interface Question {
  text: string;
  options: string[];
  answer?: number;
}

export default {
  name: 'QuizPage',
  setup() {
    let answers: Ref<(number | null)[]> = ref(new Array(15).fill(null));
    const questions = <Question[]>[
      {
        text: 'What are the prime factors of 42',
        options: ['3 × 14', '2 × 3 × 7', '2 × 21'],
        answer: 1,
      },
      {
        text: 'What are the prime factors of 150?',
        options: ['2 × 3 × 5 × 5', '3 × 3 × 5 × 5', '6 × 25'],
        answer: 0,
      },
    ];
    let activeQuestionIndex = ref(0);
    let activeQuestionItem = computed(() => {
      return questions[activeQuestionIndex.value];
    });
    let showAnswer: Ref<boolean> = ref(false);
    let isAnswerCorrect: Ref<boolean | null> = ref(null);

    const checkAnswer = () => {
      showAnswer.value = true;
      if (
        questions[activeQuestionIndex.value].answer ===
        answers.value[activeQuestionIndex.value]
      ) {
        console.log('%cCorrect', 'color: green');
        isAnswerCorrect.value = true;
      } else {
        console.log('%cWrong', 'color: red');
        isAnswerCorrect.value = false;
      }
    };

    const nextQuestion = () => {
      activeQuestionIndex.value += 1;
      reset();
    };

    const reset = () => {
      showAnswer.value = false;
      answers.value[activeQuestionIndex.value] = null;
      isAnswerCorrect.value = null;
    };

    return {
      activeQuestionIndex,
      activeQuestionItem,
      questions,
      answers,
      checkAnswer,
      showAnswer,
      isAnswerCorrect,
      nextQuestion,
      reset,
    };
  },
};
</script>
