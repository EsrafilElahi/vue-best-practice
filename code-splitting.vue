<script setup lang="ts">
import { ref, h, defineAsyncComponent } from 'vue';
const CodeSplitExampleComponent = defineAsyncComponent(() =>
    import('@/components/CodeSplitExampleComponent.vue')
)

// const CodeSplitExampleComponent = defineAsyncComponent({
//     loader: () => import('@/components/CodeSplitExampleComponent.vue'),
//     loadingComponent: h('div', 'Loading...') /* shows while loading */,
//     errorComponent: h('div', 'Error!') /* shows if there's an error */,
//     delay: 1000 /* delay in ms before showing loading component */,
//     timeout: 3000 /* timeout after this many ms */,
// })

const show = ref(false);

</script>
<template>
    <h1 class="text-3xl mb-3">Code Splitting End</h1>
    <p>Hello Code Splitting Page End</p>
    <button class="btn mb-3" @click="show = !show">Toggle Code Splitting Example</button>
    <CodeSplitExampleComponent v-if="show" />
</template>