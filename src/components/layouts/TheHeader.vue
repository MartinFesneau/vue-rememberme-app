<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
  props: ['title']
};
</script>
<style scoped>
header {
  width: 100%;
  background-color: #222831;
  height: 5rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

h1 {
  color: #ffd369;
  margin: 0;
}
</style>
