<!-- (older approach -> Before Vue 3.4) ChildComponent.vue -->
<template>
  <input
    type="text"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>

<script setup>
import { defineProps, defineEmits } from "vue";

defineProps({
  modelValue: String,
});

defineEmits(["update:modelValue"]);
</script>

<!-- (older approach -> Before Vue 3.4) ParentComponent.vue -->
<template>
  <div>
    <ChildComponent v-model="parentValue" />
    Parent Value: {{ parentValue }}
  </div>
</template>

<script setup>
import { ref } from "vue";
import ChildComponent from "./ChildComponent.vue";

const parentValue = ref("");
</script>

<!-------------------------------------------------------------------------------------------------------------

<!-- (newer approach -> After Vue 3.4) ChildComponent.vue -->
<script setup>
import { defineModel } from "vue";

const model = defineModel();
</script>

<template>
  <input type="text" v-model="model" />
</template>

<!-- (newer approach -> After Vue 3.4) ParentComponent.vue -->
<template>
  <div>
    <ChildComponent v-model="parentValue" />
    Parent Value: {{ parentValue }}
  </div>
</template>

<script setup>
import { ref } from "vue";
import ChildComponent from "./ChildComponent.vue";

const parentValue = ref("");
</script>
