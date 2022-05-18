<template>
  <div class="border border-success border-2 rounded-3 form shadow">
    <b-avatar size="10em" class="avatar mb-3 start-50 translate-middle-x"></b-avatar>
    <h1 class="text-center">Hi {{ username }}</h1>
    <p>{{ secretMessage }}</p>
    <div class="mt-3 d-flex justify-content-center">
        <b-button variant="warning" type="button" value="Logout" @click="logout">Logout</b-button>
    </div>
  </div>
</template>

<script>
import AuthService from '@/services/AuthService.js';
export default {
    name: "Home-View",
    data(){
        return{
            secretMessage: '',
            username: ''
        };
    },

    async created(){
        if(!this.$store.getters.isLoggedIn){
            this.$router.push('/login');
        }

        this.username = this.$store.getters.getUser.username;

        this.secretMessage = await AuthService.getSecretContent();
    },

    methods:{
        logout(){
            this.$store.dispatch('logout');
            this.$router.push('/login');
        }
    }
};
</script>

<style>
.avatar{
    background-color:#0d6efd;
    color:white;
}
</style>