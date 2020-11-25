<template>
  <button :type="type" :class="mode">
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: ['type', 'mode']
}
</script>

<style scoped>
  button {
    font-weight: bold;
    background-color: #222831;
    color: #ffd369;
    padding: 0.75rem 1rem;
    border-radius: 25px;
    text-decoration: none;
    font-family: inherit;
    border: 1px solid #222831;
    cursor: pointer;
      outline-style: none;
}

button:hover,
button:active {
  background-color: #393e46;
  border-color: #393e46;
}

.flat {
  background-color: transparent;
  color: #393e46;
  border: none;
}

.flat:hover,
.flat:active {
  background-color: #ffd369;
}
</style>