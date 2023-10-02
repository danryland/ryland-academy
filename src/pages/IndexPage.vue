<template>
  <q-page class="flex flex-center">
    <div class="text-center">
      <transition appear enter-active-class="animated backInDown slow"
        ><q-img
          src="../assets/img/icon-ryland-academy-white.svg"
          alt="Ryland Academy"
        />
      </transition>
      <transition appear enter-active-class="animated fadeInUp slow delay-2s">
        <h1 class="text-h3 q-mt-none">Ryland Academy</h1>
      </transition>
      <transition appear enter-active-class="animated fadeInUp delay-3s slower">
        <p class="text-h4 q-mb-xl">
          An Open Source Educational Academy
        </p></transition
      >
      <transition appear enter-active-class="animated fadeInUp slower delay-5s">
        <p class="text-bold text-grey-5">
          <small>
            Started by
            <a class="text-grey-5" href="https://twitter.com/realdanryland"
              >Dan Ryland</a
            >, founder of
            <a class="text-grey-5" href="https://ryland.wales">Ryland</a>
            <br />&amp; co-founder of
            <a class="text-grey-5" href="https://insidrmusic.com/"
              >Insidr Music</a
            ></small
          >
        </p></transition
      >
    </div>
  </q-page>
</template>

<script lang="ts">
export default {
  name: 'IndexPage',
};
</script>

<style lang="scss" scoped>
.q-img {
  max-width: 200px;
  margin-bottom: 40px;
}
</style>
