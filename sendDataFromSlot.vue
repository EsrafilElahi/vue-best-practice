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
