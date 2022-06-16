<template>
  <v-card
    :elevation="elevation"
    class="user-card"
  >
    <v-card-title>{{ name }}</v-card-title>
    <v-card-text>{{ age }}</v-card-text>
    <v-card-text>{{ description }}</v-card-text>
  </v-card>
</template>

<script lang="ts">
import Vue, { PropType } from 'vue';

export default Vue.extend({
  props: {
    name: {
      type: String as PropType<string>,
      required: false,
      default: '이름',
    },
    age: {
      type: Number as PropType<number>,
      required: false,
      default: 10,
    },
    description: {
      type: String as PropType<string>,
      required: false,
      default: '설명',
    },
    elevation: {
      type: Number,
      required: false,
      default: null,
    },
  },
});
</script>
