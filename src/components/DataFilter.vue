<template>
  <div>
    <input v-model="query" type="text" placeholder="Keresés...">
    <input v-model="newName" type="text" placeholder="Új név hozzáadása" @keyup.enter="addName">
    <button @click="addName">Hozzáadás</button>
    <ul>
      <li v-for="item in filtered" :key="item.id">{{ item.name }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      query: '',
      newName: '',
      data: [
        { id: 1, name: 'John Doe' },
        { id: 2, name: 'Jane Doe' },
        { id: 3, name: 'Jim Smith' },
        { id: 4, name: 'Sarah Johnson' }
      ]
    }
  },
  computed: {
    filtered() {
      let q = this.query.toLowerCase()
      return this.data.filter(d => d.name.toLowerCase().indexOf(q) !== -1)
    }
  },
  methods: {
    addName() {
      if (this.newName.trim() === '') return

      let newId = this.data.length + 1
      this.data.push({ id: newId, name: this.newName.trim() })
      this.newName = ''
    }
  },
  watch: {
    query(val) {
      console.log('filter changed:', val)
    }
  }
}
</script>

<style scoped></style>s