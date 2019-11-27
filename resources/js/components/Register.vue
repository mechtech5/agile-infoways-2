<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Register</div>

                    <div class="row mt-3">
                      <form class="col-6 offset-3">
                        <div class="form-group">
                          <input type="text" v-model="name" class="form-control" placeholder="Name">
                        </div>
                        <div class="form-group">
                          <input type="email" v-model="email" class="form-control" placeholder="Email">
                        </div>
                        <div class="form-group">
                          <input type="password" v-model="password" class="form-control" placeholder="Password">
                        </div>
                        <div class="form-group">
                          <input type="password" v-model="c_password" class="form-control" placeholder="Confirm Password">
                        </div>
                        <div class="form-group">
                          <div class="text-center">
                            <a class="btn btn-primary" @click.prevent="Register()">Register</a>
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
      data()
      {
        return {
          name: '',
          email: '',
          password: '',
          c_password: ''
        }
      },
      methods: {
        Register() {
          axios.post('/api/register', {
            'name': this.name,
            'email': this.email,
            'password': this.password,
            'c_password': this.c_password
          }).then(response => {
            console.log(response.data);
            localStorage.setItem("user", response.data.user);
            window.location.href = '/articles';
          }).catch(error => {

            console.log(error.response.data);
          });
        }
      }
    }
</script>