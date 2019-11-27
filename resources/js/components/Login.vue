<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Login</div>

                    <div class="row mt-3">
                      <form class="col-6 offset-3">
                        <div class="form-group">
                          <input type="text" v-model="email" class="form-control" placeholder="Name">
                        </div>
                        <div class="form-group">
                          <input type="password" v-model="password" class="form-control" placeholder="Password">
                        </div>
                        <div class="form-group">
                          <div class="text-center">
                            <a class="btn btn-primary" @click.prevent="Login()">Login</a>
                          </div>
                        </div>
                      </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
      data() {
        return {
          email: '',
          password: ''
        }
      },
      methods: {
        Login() {
          axios.post('/api/login', {
            'email': this.email,
            'password': this.password
          }).then(response => {
            console.log(response.data);
            localStorage.setItem("user", JSON.stringify(response.data.user));
            window.location.href = '/articles';
          }).catch(error => {
            console.log(error.response.data);
          });
        }
      }
    }
</script>