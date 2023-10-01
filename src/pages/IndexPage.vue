<template>
  <q-page>
    <div class="q-pa-lg">
      <h1 class="text-h3 q-ma-none">Ryland Academy</h1>
      <router-link :to="{ name: 'learn' }">Learn</router-link>
    </div>
  </q-page>
</template>

<script lang="ts">
export default {
  name: 'IndexPage',
};
</script>
