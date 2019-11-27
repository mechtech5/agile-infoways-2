<template>
  <nav class="navbar navbar-expand-md navbar-light navbar-laravel">
    <div class="container">
        <a class="navbar-brand" href="#">
           Laravel
        </a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent">
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <!-- Left Side Of Navbar -->
            <ul class="navbar-nav mr-auto">

            </ul>

            <!-- Right Side Of Navbar -->
            <ul class="navbar-nav ml-auto">
                <!-- Authentication Links -->
                <span v-if="isEmpty(auth)">
                    <li class="nav-item" >
                        <a class="nav-link" href="/login">Login</a>
                    </li>
                    
                    <li class="nav-item">
                        <a class="nav-link" href="/register">Register</a>
                    </li>
                </span>
                <span v-else>    
                    <li class="nav-item dropdown">
                        <a id="navbarDropdown" class="nav-link dropdown-toggle" href="#" role="button" data-toggle="dropdown">
                            {{ auth.name }} <span class="caret"></span>
                        </a>

                        <div class="dropdown-menu dropdown-menu-right" aria-labelledby="navbarDropdown">
                            <a class="dropdown-item" href="#"
                              @click.prevent="Logout()">
                                Logout
                            </a>
                        </div>
                    </li>
                </span>
            </ul>
        </div>
    </div>
  </nav>
</template>

<script>
  export default {
    data() {
      return {
        auth: {}
      }
    },
    mounted() {
      this.checkAuth();
    },
    methods: {
      checkAuth() {
        let user = localStorage.getItem("user");
        this.auth = (!this.isEmpty(user)) ? JSON.parse(user) : {};
      },

      Logout() {
        localStorage.removeItem("user");
        this.auth = {};
        window.location.href = '/login';
      },

      isEmpty(obj) {
		    for(var key in obj) {
	        if(obj.hasOwnProperty(key))
	          return false;
		    }
		    return true;
			},
    }
  }
</script>

