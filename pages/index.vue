<template>
  <div class="index-page">
    <v-row>
      <v-col
        :lg="3"
        :md="4"
        :sm="12"
      >
        <user-list
          :items="users"
          :active-index="selectedIndex"
          @click:item="onClickItem"
        ></user-list>
      </v-col>
      <v-col
        :lg="9"
        :md="8"
        :sm="12"
      >
        <user-editor
          v-if="selectedItem"
          :name.sync="selectedItem.name"
          :age.sync="selectedItem.age"
          :description.sync="selectedItem.description"
        >
          <template #title>제목</template>
        </user-editor>
      </v-col>
    </v-row>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

type ItemType = {
  name: string,
  age: number,
  description: string,
};

export default Vue.extend({
  name: 'IndexPage',
  data() {
    return {
      selectedIndex: -1 as number,
      users: [
        { name: '박찬영', age: 25, description: '설명' },
        { name: '테스트1', age: 25, description: '설명' },
        { name: '테스트2', age: 25, description: '설명' },
        { name: '테스트3', age: 25, description: '설명' },
      ] as ItemType[],
    };
  },
  computed: {
    selectedItem(): ItemType | null {
      if (this.selectedIndex < 0) return null;
      return this.users[this.selectedIndex]; 
    },
  },
  methods: {
    onClickItem(_: any, index: number) {
      this.selectedIndex = index;
    },
  },
});
</script>