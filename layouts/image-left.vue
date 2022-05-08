<script setup lang="ts">
import { computed } from "vue";
const props = defineProps({
  image: {
    type: String,
  },
  class: {
    type: String,
  },
  href: {
    type: String,
  },
  maxWidth: {
    type: String,
  },
  caption: {
    type: String,
  },
});
const style = computed(() => {
  return { "max-width": props.maxWidth };
});
</script>

<template>
  <div class="grid grid-cols-2 w-full h-full">
    <div class="image-left h-full grid place-content-center">
      <a v-if="href" :href="href">
        <img class="m-auto border-radius" :style="style" :src="image" />
        <p class="text-3xl text-center font-semibold">
          {{ caption }}
        </p>
      </a>
      <div v-else>
        <img class="m-auto border-radius" :style="style" :src="image" />
        <p class="text-3xl text-center font-semibold">
          {{ caption }}
        </p>
      </div>
    </div>
    <div
      class="slidev-layout image-left center h-full grid place-content-center"
      :class="props.class"
    >
      <div class="my-auto w-full text-center">
        <slot />
      </div>
    </div>
  </div>
</template>
