<template>
  <q-page class="row items-center">
    <h1 class="sr-only">Ryland Academy</h1>
    <div class="flex col-12 col-6-md items-center stretch justify-center">
      <div class="card card-main">
        <h2>Prime factors</h2>
        <p>
          <strong>Prime numbers</strong> are unique because they can only be
          divided by 1 and themselves, leaving no leftovers or remainders.
        </p>
        <p>
          <strong>Prime factors</strong> are special prime numbers that, when
          multiplied together, create a larger number, known as a
          <strong>composite number</strong>.
        </p>
        <p>
          <strong>Prime factorisation</strong> is the process of breaking a
          number down into its prime numbers, which are like the fundamental
          building blocks that, when multiplied, reconstruct the original
          number.
        </p>
      </div>
    </div>
    <div class="col col-12 col-6-md stretch">
      <div class="row stretch height-50">
        <div class="column stretch">
          <div class="card card-one height-50">
            <h3>Prime numbers</h3>
            <p>2 3 5 7 11 13...</p>
          </div>
          <div class="card card-two height-50">
            <h3>Composite number</h3>
            <p>20</p>
          </div>
        </div>
        <div class="card card-three stretch flex col">
          <h3>Prime factors</h3>
          <p>2 x 2 x 5</p>
        </div>
      </div>
      <div class="row stretch height-50">
        <div class="card card-four stretch">
          <h3>Prime factorisation (Factor tree)</h3>
          <q-img
            style="width: 250px; height: auto"
            fit="contain"
            src="../assets/img/prime-factors.svg"
            alt=""
          />
        </div>
      </div>
    </div>
  </q-page>
</template>

<script lang="ts">
import { Todo, Meta } from 'components/models';
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'IndexPage',
  setup() {
    const todos = ref<Todo[]>([
      {
        id: 1,
        content: 'ct1',
      },
      {
        id: 2,
        content: 'ct2',
      },
      {
        id: 3,
        content: 'ct3',
      },
      {
        id: 4,
        content: 'ct4',
      },
      {
        id: 5,
        content: 'ct5',
      },
    ]);
    const meta = ref<Meta>({
      totalCount: 1200,
    });
    return { todos, meta };
  },
});
</script>
