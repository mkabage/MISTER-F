<template>
  <div class="container">
    <div
      id="login-form"
      class="row"
    >
      <div class="col-md-4 offset-md-4">
        <h4>Login</h4>
        <form>
          <div class="form-group">
            <label for="email">Email address</label>
            <input
              id="email"
              v-model="email"
              autofocus
              type="email"
              class="form-control"
              aria-describedby="emailHelp"
              placeholder="Enter email"
            >
            <small
              v-if="invalidEmail"
              class="text-danger"
            >Invalid email</small>
            <small
              id="emailHelp"
              class="form-text text-muted"
            >We'll never share your email with anyone else.</small>
          </div>
          <div class="form-group">
            <label for="password">Password</label>
            <input
              id="password"
              v-model="password"
              type="password"
              class="form-control"
              placeholder="Password"
            >
          </div>

          <div>
            <small
              v-if="invalidCredentials"
              class="text-danger"
            >Invalid credentials</small>
          </div>

          <button
            type="submit"
            class="btn btn-primary"
            @click="handleSubmit"
          >
            Submit
          </button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      email: '',
      password: '',
      invalidEmail: false,
      invalidCredentials: false
    }
  },
  methods: {
    handleSubmit (e) {
      e.preventDefault()
      const isEmail = (this.email.includes('@') && this.email.includes('.'))
      this.invalidEmail = false
      this.invalidCredentials = false

      if (isEmail && this.password.length > 0) {
        this.$http.post(`${process.env.BACKEND_URL}/users/login`, {
          email: this.email,
          password: this.password
        })
          .then(response => {
            let usersData = response.data
            localStorage.setItem('userName', usersData.user._id)
            this.$router.push('dashboard')
          })
          .catch(function (error) {
            this.invalidCredentials = true
            console.error(error.response)
          })
      } else {
        this.invalidEmail = true
      }
    }
  }
}

</script>
