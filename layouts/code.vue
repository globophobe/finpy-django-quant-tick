<script setup lang="ts">
const props = defineProps({
  text: {
    type: String,
  },
  trans: {
    type: String,
  },
});
</script>

<template>
  <div class="slidev-layout code h-full grid place-content-center">
    <div class="my-auto w-full text-center">
      <h1 v-html="text"></h1>
      <p v-html="trans"></p>
      <div class="text-left">
        <slot />
      </div>
    </div>
  </div>
</template>
