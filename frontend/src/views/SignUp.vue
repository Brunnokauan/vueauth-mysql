<template>
  <div>
    <h1 class="text-center">Sign Up</h1>
    <b-form class="border border-success border-2 rounded-3 form shadow"> 
        <b-form-group label="Usename:">
            <b-form-input type="text" v-model="username" placeholder="type your username"/>
        </b-form-group>
        <b-form-group class="my-3" label="Password:">
            <b-form-input type="password" v-model="password" placeholder="type your password"/>
        </b-form-group>
        <b-form-group label="Password (repeat):">
            <b-form-input type="password" v-model="password_repeat" placeholder="repeat your password"/>
        </b-form-group>

        <div class="mt-3 d-flex justify-content-center">
            <b-button variant="success" type="button" @click="signUp" value="Sign Up">SignUp</b-button>
        </div>
        <p v-if="msg" class="msg text-center mt-3 fw-bold fs-6">{{ msg }}</p>
    </b-form>
  </div>
</template>

<script>
import AuthService from '@/services/AuthService.js';
export default {
    data(){
        return{
            username: "",
            password: "",
            password_repeat: "",
            msg: ""
        };
    },

    methods:{
        async signUp(){
            try{
                const credentials = {
                    username: this.username,
                    password: this.password,
                    password_repeat: this.password_repeat
                };
                const response = await AuthService.signUp(credentials);
                this.msg = response.msg;
                this.$router.push('/');
            } catch (error) {
                this.msg = error.response.data.msg;
            }
        }
    }
};
</script>

<style>
.form{
    padding: 20px;
    margin-top: 3%;
    margin-inline: 35%;
    background-color: white;
}

.msg{
    color: red;
}
</style>