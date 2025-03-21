// child file
<ul>
  <li v-for="item in items">
    <slot name="item" v-bind="item"></slot>
  </li>
</ul>

// parent file
<template #item="{ body, username, likes }">
  <div class="item">
    <p>{{ body }}</p>
    <p>by {{ username }} | {{ likes }} likes</p>
  </div>
</template>



// ==================== another mesla ======================
// child component
<script setup>
const greetingMessage = 'hello'
</script>

<template>
  <div>
  	<slot :text="greetingMessage" :count="1"></slot>
	</div>
</template>


// parent component
<script setup>
import MyComponent from './MyComponent.vue'
</script>

<template>
	<MyComponent v-slot="slotProps">
  	{{ slotProps.text }} {{ slotProps.count }}
  </MyComponent>
</template>