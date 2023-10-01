<template>
  <q-page class="page-quiz">
    <q-linear-progress
      rounded
      size="12px"
      :value="quizProgress"
      color="green"
      class="progress"
    />
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
      label="Check answer"
      @click="checkAnswer()"
    />
    <q-btn
      v-if="
        answers[activeQuestionIndex] != null &&
        showAnswer &&
        activeQuestionIndex + 1 != totalSteps
      "
      class="btn-large full-width"
      color="green"
      rounded
      no-caps
      label="Next question"
      @click="nextQuestion()"
    />
    <q-btn
      v-if="
        answers[activeQuestionIndex] != null &&
        showAnswer &&
        activeQuestionIndex + 1 == totalSteps
      "
      class="btn-large full-width"
      color="primary"
      rounded
      no-caps
      label="Done"
      :to="{ name: 'learn' }"
    />
  </q-page>
  <q-footer class="footer-quiz">
    <q-btn
      class="full-width"
      flat
      rounded
      no-caps
      label="Learn about factors"
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
        text: 'Select the prime number',
        options: ['3', '4', '20'],
        answer: 1,
      },
      {
        text: 'Select the composite number',
        options: ['2', '4', '5'],
        answer: 2,
      },
      {
        text: 'What are the prime factors of 42',
        options: ['3 × 14', '2 × 3 × 7', '2 × 21'],
        answer: 2,
      },
      {
        text: 'What are the prime factors of 150?',
        options: ['2 × 3 × 5 × 5', '3 × 3 × 5 × 5', '6 × 25'],
        answer: 1,
      },
      {
        text: 'What is the LCM of 13 and 3?',
        options: ['13', '3', '39'],
        answer: 3,
      },
      {
        text: 'What is the HCF of 32 and 24?',
        options: ['2', '8', '4'],
        answer: 2,
      },
      {
        text: 'What is the LCM of 24 and 36?',
        options: ['12', '72', '30'],
        answer: 2,
      },
      {
        text: 'What is the HCF of 104 and 136?',
        options: ['8', '12', '13'],
        answer: 1,
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
      const currentAnswer = answers.value[activeQuestionIndex.value];
      if (
        currentAnswer !== null &&
        questions[activeQuestionIndex.value].answer === currentAnswer + 1
      ) {
        console.log('%cCorrect', 'color: green');
        isAnswerCorrect.value = true;
      } else {
        console.log('%cWrong', 'color: red');
        isAnswerCorrect.value = false;
      }
    };

    const totalSteps = ref(questions.length);
    const activeStep = computed(() => activeQuestionIndex.value + 1);
    const quizProgress = computed(() => activeStep.value / totalSteps.value);

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
      quizProgress,
      totalSteps,
    };
  },
};
</script>
