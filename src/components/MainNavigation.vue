<template>
  <ul>
    <li v-for="item in menu" :key="item.text">
      <a :href="item.url">{{ item.text }}</a>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'MainNavigation',
  data() {
    return {
      menu: [
        { text: 'Vue.js', url: 'https://vuejs.org/' },
        { text: 'React', url: 'https://reactjs.org/' },
        { text: 'Angular', url: 'https://angular.io/' },
        { text: 'Svelte', url: 'https://svelte.dev/' }
      ]
    }
  }
}
</script>

<style scoped>
ul { list-style: none; padding: 0; display: flex; gap: 15px; }
a { text-decoration: none; color: #333; font-weight: 500; }
</style>