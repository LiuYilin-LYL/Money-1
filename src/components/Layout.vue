<template>
  <div class="nav-wrapper">
    <div class="content">
      <slot></slot>
    </div>
    <Nav></Nav>
  </div>
</template>

<script lang="ts">
export default {
  name: "Layout"
}
</script>

<style scoped>
.nav-wrapper {
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