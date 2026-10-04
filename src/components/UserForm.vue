<template>
  <form @submit.prevent="submitForm">
    <div>
      <input v-model="form.username" placeholder="Username">
      <span v-if="errors.username">{{ errors.username }}</span>
    </div>

    <div>
      <input v-model="form.password" type="password" placeholder="Password">
      <span v-if="errors.password">{{ errors.password }}</span>
    </div>

    <div>
      <input v-model="form.confirmPassword" type="password" placeholder="Confirm">
      <span v-if="errors.confirmPassword">{{ errors.confirmPassword }}</span>
    </div>

    <button type="submit">Submit</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      form: { username: '', password: '', confirmPassword: '' },
      errors: {}
    }
  },
  methods: {
    validate() {
      let err = {}
      let u = this.form.username
      let p = this.form.password
      let c = this.form.confirmPassword

      if (u.length < 5 || u === p) {
        err.username = 'Username must be at least 5 characters long and different from password'
      }

      if (p.length < 8 || p === u) {
        err.password = 'Password must be at least 8 characters long and different from username'
      }

      if (c.length < 8 || c !== p) {
        err.confirmPassword = 'Confirm password must be at least 8 characters long and match with password'
      }

      this.errors = err
      return Object.keys(err).length === 0
    },

    submitForm() {
      if (!this.validate()) return

      console.log('Form submitted:', this.form)
      alert('Ok!')
      this.form = { username: '', password: '', confirmPassword: '' }
      this.errors = {}
    }
  }
}
</script>

<style scoped></style>