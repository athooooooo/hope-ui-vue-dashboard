<template>
  <div>
    <section class="login-content">
      <div class="row m-0 align-items-center bg-white vh-100">
        <div class="col-md-6">
          <div class="row justify-content-center">
            <div class="col-md-10">
              <div
                class="card card-transparent shadow-none d-flex justify-content-center mb-0 auth-card"
              >
                <div class="card-body">
                  <router-link
                    :to="{ name: 'default.dashboard' }"
                    class="navbar-brand d-flex align-items-center mb-3"
                  >
                    <img
                      src="@/assets/images/dashboard/jualbareng.png"
                      class="rounded mx-auto d-block w-25 p3"
                      alt="logo"
                      sizes="10%"
                    />
                  </router-link>
                  <h2 class="mb-2 text-center">Sign In</h2>
                  <p class="text-center">Stay Connect and Happy Working.</p>
                  <form @submit="login()"></form>

                  <div class="row">
                    <div class="col-lg-12">
                      <div class="form-group">
                        <label for="email" class="form-label">Email</label>
                        <input
                          type="email"
                          class="form-control"
                          id="email"
                          v-model="email"
                          placeholder=" "
                        />
                      </div>
                    </div>
                    <div class="col-lg-12">
                      <div class="form-group">
                        <label for="password" class="form-label"
                          >Password</label
                        >
                        <input
                          type="password"
                          class="form-control"
                          id="password"
                          v-model="password"
                          placeholder=" "
                        />
                      </div>
                    </div>
                    <div v-if="success" id="success">Logged in Succesfully</div>
                    <div v-if="error">
                      {{ error }}
                    </div>
                    <div class="col-lg-12 d-flex justify-content-between">
                      <div class="form-check mb-3">
                        <input
                          type="checkbox"
                          class="form-check-input"
                          id="customCheck1"
                        />
                        <label class="form-check-label" for="customCheck1"
                          >Remember Me</label
                        >
                      </div>
                      <router-link :to="{ name: 'auth.recoverPassword' }"
                        >Forgot Password?</router-link
                      >
                    </div>
                  </div>
                  <div class="d-flex justify-content-center">
                    <router-link
                      to="/default"
                      class="btn btn-primary"
                      v-on:click="login()"
                      >SignIn</router-link
                    >
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="sign-bg">
            <img
              src="@/assets/images/dashboard/jualbareng.png"
              class="w-100% col-12 opacity-25"
              alt="bg"
            />
          </div>
        </div>
        <div
          class="col-md-6 d-md-block d-none bg-primary p-0 mt-n1 vh-100 overflow-hidden"
        >
          <img
            src="@/assets/images/auth/01.png"
            class="img-fluid gradient-main animated-scaleX"
            alt="images"
          />
        </div>
      </div>
    </section>
  </div>
</template>
<script>
import axios from 'axios'

export default {
  data () {
    return {
      postBody: '',
      errors: []

    }
  },

  methods: {
    // Pushes posts to the server when called.
    async login () {
      const formData = new FormData()
      formData.append('email', 'info@jualbareng.com')
      formData.append('password', 'infojb123')
      try {
        await axios
          .post('https://api-staging.jualbareng.com/admin/login', formData, {
            headers: {
              'Content-Type': 'multipart/form-data'
            }
          })
          .then((response) => console.log(response))
      } catch (e) {
        this.errors.push(e)
        console.log('error gagal hits api')
      }
    }
  }
  //   created () {
  //     this.login()
  //   }
}
</script>
