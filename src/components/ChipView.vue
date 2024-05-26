<script setup lang="ts">
import { defineProps, withDefaults } from "vue";
import type { VChip } from "vuetify/components";
type TVariant = VChip["$props"]["variant"];

interface Props {
  text?: string;
  color: string;
  variant?: TVariant;
  class?: string;
  size?: string;
  icon?: string;
}

const props = withDefaults(defineProps<Props>(), {
  text: undefined,
  color: undefined,
  variant: "outlined",
  size: undefined,
  icon: undefined,
});
</script>
<template>
  <v-chip
    :class="props.class"
    :color="props.color"
    :variant="props.variant"
    :prepend-icon="props.icon"
    :size="props.size"
  >
    {{ props.text }}
  </v-chip>
</template>
