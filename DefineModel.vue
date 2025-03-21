// ============== child ==============
<template>
  <input v-model="model" />
</template>

<script setup>
import { defineModel } from "vue";

const model = defineModel();
</script>

// ============== parent ==============
<template>
  <ChildComponent v-model="parentModel" />
</template>

<script setup>
import { ref } from "vue";

const parentModel = ref("Initial Value");
</script>
