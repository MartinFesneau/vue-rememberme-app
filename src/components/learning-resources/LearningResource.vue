<template>
  <li>
    <base-card>
      <header>
        <h3>{{ title }}</h3>
        <base-button mode="flat" @click="deleteResource(id)"><i class="fas fa-trash"></i></base-button>
      </header>
    <p>{{ description }}</p>
    <nav>
      <a :href="link" target="blank">View resource</a>
    </nav>
    </base-card>
  </li>
</template>

<script>
export default {
  inject: ['deleteResource'],
  props: {
    id: {
      type: String,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    description: {
      type: String,
      required: true
    },
    link: {
      type: String,
      required: true
    }
  },
}
</script>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color:#c89300;
}

a:hover,
a:active {
  color:  #ce5c00;
}
</style>