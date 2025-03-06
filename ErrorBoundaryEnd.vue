<script setup lang="ts">
const error = ref();
onErrorCaptured((err) => {
  console.log("error captured from slot", err);
  error.value = err;
  return false;
});

function clearError() {
  error.value = null;
}

const slotProps = computed(() => {
  if (!error.value) return {};
  return { error, clearError };
});

const slotName = computed(() => (error.value ? "error" : "default"));
</script>
<template>
  <slot :name="slotName" v-bind="slotProps"></slot>
</template>


<template #error="{ error, clearError }">
  <div>
    خطایی رخ داده است: {{ error.message }}
    <button @click="clearError">پاک کردن خطا</button>
  </div>
</template>

<!-- ErrorBoundaryEnd -->
<ErrorBoundaryEnd>
  <template #default>
    <!-- محتوای اصلی -->
  </template>
  <template #error="{ error, clearError }">
    <!-- پیام خطا با دکمه پاک کردن -->
  </template>
</ErrorBoundaryEnd>

<!-- RandomErrorWithSlots -->
<RandomErrorWithSlots>
  <!-- محتوای اصلی -->
</RandomErrorWithSlots>
