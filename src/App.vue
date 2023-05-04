<script>
import BasicExample from './components/BasicExample.vue'
import TheWelcome from './components/TheWelcome.vue'

const routes = {
  '/': BasicExample
}

export default {
  data() {
    return {
      currentPath: window.location.hash
    }
  },
  computed: {
    currentView() {
      return routes[this.currentPath.slice(1) || '/'] || TheWelcome
    }
  },
  mounted() {
    window.addEventListener('hashchange', () => {
      this.currentPath = window.location.hash
    })
  }
}
</script>

<template>
  <a href="#/">Basic Example</a> | <a href="#/actor">Spawning Actors</a> |
  <component :is="currentView" />
</template>
