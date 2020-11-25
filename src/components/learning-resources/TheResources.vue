<template>
  <base-card class="tabs">
    <base-button 
      @click="setSelectedTab('stored-resources')"
      :mode="storeResButtonMode"
      >Stored Resources</base-button>
    <base-button
    @click="setSelectedTab('add-resources')"
    :mode="addResButtonMode"
    >Add resources</base-button>
  </base-card>
  <keep-alive>
    <component :is="selectedTab" @add-new-resource="addResource"></component>
  </keep-alive>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResources from './AddResources.vue'

export default {
  components: {
    StoredResources,
    AddResources
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedRessources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js documentation',
          link: 'https://vuejs.org'
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to Google',
          link: 'https://google.com'
        }
      ]
    };
  },
  provide() {
    return {
      resources: this.storedRessources,
      addResource: this.addResource,
      deleteResource: this.removeResource,
    }
  },
  computed: {
    storeResButtonMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat'
    },
    addResButtonMode() {
      return this.selectedTab === 'add-resources' ? null : 'flat'
    }
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, link) {
      const newRes = {
        id: new Date().toISOString,
        title,
        description,
        link
      };
      this.storedRessources.unshift(newRes);
      this.selectedTab = 'stored-resources'
    },
    removeResource(id) {
      const resIndex = this.storedRessources.findIndex(res => res.id === id);
      this.storedRessources.splice(resIndex, 1);
    },
  }
}
</script>

<style scoped>
.tabs {
  display: flex;
  justify-content: space-around;
}
</style>