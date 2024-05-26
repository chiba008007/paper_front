<script setup lang="ts">
import { defineProps, withDefaults } from "vue";

interface Props {
  text?: string;
  class?: string;
}

const props = withDefaults(defineProps<Props>(), {
  text: undefined,
  class: undefined,
});
</script>
<template>
  <p :class="props.class">{{ props.text }}</p>
</template>
