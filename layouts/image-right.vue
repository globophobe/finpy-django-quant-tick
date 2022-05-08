<script setup lang="ts">
const props = defineProps({
  text: {
    type: String,
  },
  trans: {
    type: String,
  },
  href: {
    type: String,
  },
  caption: {
    type: String,
  },
});
</script>

<template>
  <div class="grid grid-cols-2 w-full h-full">
    <div
      class="slidev-layout image-right center h-full grid place-content-center"
      :class="props.class"
    >
      <div class="my-auto w-full text-center">
        <h1 v-html="text"></h1>
        <p v-html="trans"></p>
      </div>
    </div>
    <div class="image-right h-full grid place-content-center">
      <a v-if="href" :href="href">
        <slot />
        <p class="text-3xl text-center font-semibold">
          {{ caption }}
        </p>
      </a>
      <div v-else>
        <slot />
        <p class="text-3xl text-center font-semibold">
          {{ caption }}
        </p>
      </div>
    </div>
  </div>
</template>
