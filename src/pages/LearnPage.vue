<template>
  <q-page class="page-learn">
    <h1>Prime factors</h1>
    <p>
      <strong>Prime numbers</strong> are unique because they can only be divided
      by 1 and themselves, leaving no leftovers or remainders.
    </p>
    <p>
      <strong>Prime factors</strong> are special prime numbers that, when
      multiplied together, create a larger number, known as a
      <strong>composite number</strong>.
    </p>
    <p>
      <strong>Prime factorisation</strong> is the process of breaking a number
      down into its prime numbers, which are like the fundamental building
      blocks that, when multiplied, reconstruct the original number.
    </p>
    <h2>Highest common factor</h2>
    <p>
      The <strong>highest common factor (HCF)</strong> the biggest number that
      can evenly divide both of your numbers.
    </p>
    <h2>Lowest common multiple</h2>
    <p>
      The <strong>lowest/least common multiple (LCM)</strong> is the smallest
      number that both of your numbers can fit into evenly.
    </p>
  </q-page>
  <q-footer class="footer-learn">
    <q-btn
      class="btn-large full-width"
      color="primary"
      rounded
      no-caps
      label="Start quiz"
      :to="{ name: 'quiz' }"
    />
  </q-footer>
</template>

<script lang="ts">
export default {
  name: 'LearnPage',
};
</script>
