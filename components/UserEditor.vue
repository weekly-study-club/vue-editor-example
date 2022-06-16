<template>
  <v-card class="user-editor">
    <v-form>
      <v-card-title>
        <slot name="title">유저 편집기</slot>
      </v-card-title>
      <v-card-text>
        <v-text-field
          :value="name"
          :label="nameLabel"
          @input="onChangeValue('name', $event)"
        ></v-text-field>
        <v-text-field
          type="number"
          :value="age"
          :label="ageLabel"
          @input="onChangeValue('age', $event)"
        ></v-text-field>
        <v-textarea
          :value="description"
          :label="descriptionLabel"
          @input="onChangeValue('description', $event)"
        ></v-textarea>
      </v-card-text>
    </v-form>
  </v-card>  
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  props: {
    name: {
      type: String,
      required: false,
      default: null,
    },
    nameLabel: {
      type: String,
      required: false,
      default: '이름',
    },
    age: {
      type: Number,
      required: false,
      default: null,
    },
    ageLabel: {
      type: String,
      required: false,
      default: '나이',
    },
    description: {
      type: String,
      required: false,
      default: null,
    },
    descriptionLabel: {
      type: String,
      required: false,
      default: '설명',
    },
  },
  methods: {
    onChangeValue(key: string, value: any) {
      this.$emit(`update:${key}`, value);
    },
  },
});
</script>
