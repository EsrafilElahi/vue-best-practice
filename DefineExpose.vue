// ------- child component ---------
<template>
  <div>
    <button @click="increment">{{ count }}</button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const count = ref(0);
const increment = () => {
  count.value++;
};

const double = () => {
  count.value *= 2;
};

defineExpose({
  increment,
  count,
});
</script>

// ------- parent component ---------
<template>
  <div>
    <ChildComponent ref="child" />
    <button @click="onChildClick">Call Child's Increment Method</button>
    <p>Child's Count: {{ childCount }}</p>
  </div>
</template>

<script setup>
import ChildComponent from "./ChildComponent.vue";
import { ref, onMounted } from "vue";

const child = ref(null);
const childCount = ref(0);

const onChildClick = () => {
  child.value.increment();
};

onMounted(() => {
  childCount.value = child.value.count;
});
</script>
