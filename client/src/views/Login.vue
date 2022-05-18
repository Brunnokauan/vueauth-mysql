<template>
  <div>
    <h1 class="text-center text" >Login</h1>
    <b-form class="border border-success border-2 rounded-3 form shadow"> 
        <b-form-group label="Usename:">
            <b-form-input type="text" v-model="username" placeholder="type your username"/>
        </b-form-group>
        <b-form-group class="my-3" label="Password:">
            <b-form-input type="password" v-model="password" placeholder="type your password"/>
        </b-form-group>

        <div class="mt-3 d-flex justify-content-center">
            <b-button variant="success" type="button" @click="login" value="Login">Login</b-button>
        </div>
        <p v-if="msg" class="msg text-center mt-3 fw-bold fs-6">{{ msg }}</p> 
    </b-form>
    
  </div>
</template>

<script>
import AuthService from '@/services/AuthService.js';
export default {
    name: 'Login-View',
    data(){
        return{
            username:'',
            password:'',
            msg: ''
        };
    }, 
    methods:{
        async login(){
            try{
                const credentials = {
                    username: this.username,
                    password: this.password
                };
                const response = await AuthService.login(credentials);
                this.msg = response.msg
                
                const token = response.token;
                const user = response.user;

                this.$store.dispatch('login', {token, user});
                this.$router.push('/');
            } catch (error) {
                this.msg = error.response.data.msg;
            }
        }
    }
};
</script>

<style>
.msg{
    color: red;
}
</style>