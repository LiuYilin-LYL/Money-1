<template>
  <div class="layout-wrapper" :class="classPrefix &&`${classPrefix}-wrapper`">
    <div class="content" :class="classPrefix &&`${classPrefix}-content`">
      <slot></slot>
    </div>
    <Nav></Nav>
  </div>
</template>

<script lang="ts">
export default {
  props:["classPrefix"],
  name: "Layout"
}
</script>

<style scoped>
.layout-wrapper {
  border: 1px solid blue;
  display: flex;
  flex-direction: column;
  height: 100vh
}
.content {
  border: 1px solid yellowgreen;
  overflow: auto;
  flex-grow: 1;
}
</style>