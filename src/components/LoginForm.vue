<template>
<div style="background-color:#231F20; min-height:100vh;">
	<b-navbar style="color:#231F20; background-color:#B79A62; border-color:#231F20;">
		<b-navbar-brand><b><font face = "Verdana" size ="6">Yeet Another Contact Manager</font></b></b-navbar-brand>
		<b-navbar-nav class="ml-auto"></b-navbar-nav>
		<img src="./UCF_Pegasus_Logo.jpg" alt="UCF Pegasus">
	</b-navbar>
	<br></br>
    <b-container>
        <b-card style="background-color:#231F20; border-color:#B79A62;">
            <h2 style="color:#F2C413;">Login</h2>
            <b-form @submit="onSubmit" v-if="show">
            <b-form-group style="color:#F2C413;" id="username" label="Username:" label-for="username">
                <b-form-input id="username" type="text" v-model="form.username" required placeholder="Enter username">
                </b-form-input>
            </b-form-group>
            <b-form-group style="color:#F2C413;" id="password" label="Password:" label-for="password">
                <b-form-input id="password" type="password" v-model="form.password" required placeholder="Enter password">
                </b-form-input>
            </b-form-group>
            <b-button style="color:#231F20; background-color:#B79A62; border-color:#231F20;" type="submit" variant="primary"><b>Login</b></b-button>
            <b-button style="color:#231F20; background-color:#B79A62; border-color:#231F20;" type="reset" variant="danger" @click="routeRegister()"><b>Don't have an account?</b></b-button>
            </b-form>
        </b-card>
    </b-container>
  </div>
</template>

<script>
import router from '../router'
import axios from 'axios'

export default {
data () {
    return {
      form: {
        username: '',
        password: '',
      },
      show: true
    }
  },

  methods: {

    onSubmit (evt) {
      evt.preventDefault();

      // Store the username and password in 2 variables
      var formPayload = {
        username: this.form.username,
        password: this.form.password,
      }

      // Axios POST call using (url, formpayload above)
      let uri = 'http://:3000/user/login';
      axios.post(uri, formPayload).then(function(response) {


        // After login submission we we want to redirect the page to the contacts home page
        router.push('/contactshome');
      });


    },

    routeRegister() {
      router.push('/register');
    }
  }
}
</script>

<style>

</style>
