<template>
  <ul class="user-list">
    <li
      v-for="(item, key) in items"
      :key="key"
      class="mb-2"
      @click="onClickItem(item, key)"
    >
      <user-card
        :class="{ active: key === activeIndex }"
        :name="item.name"
        :age="item.age"
        :description="item.description"
      ></user-card>
    </li>
  </ul>
</template>

<script lang="ts">
import Vue, { PropType } from 'vue';

export default Vue.extend({
  props: {
    activeIndex: {
      type: Number,
      required: false,
      default: null,
    },
    items: {
      type: Array as PropType<any[]>,
      required: false,
      default: () => [],
    },
  },
  methods: {
    onClickItem(item: any, key: number) {
      this.$emit('click:item', item, key);
    },
  },
});
</script>

<style scoped>
  .user-list {
    list-style: none;
    padding: 0;
  }
  .active {
    border: 1px solid red;
  }
</style>
