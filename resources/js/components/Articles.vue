<template>
    <div class="container">
        <div class="row justify-content-center">
            <p v-if="!isEmpty(auth)">My Articles</p>
        </div>
    </div>
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