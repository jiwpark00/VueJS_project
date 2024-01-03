<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      validEmail: false,
      validPassword: false,
      emailMessage: '',
      passwordMessage: ''
    }
  },
  methods: {
    onSubmit(e) {
      this.validEmail = false;
      if (this.email.length < 6) {
        this.emailMessage = "Email should be minimum of 6 characters";
      }
      else if (this.email.indexOf(' ') >= 0) {
        this.emailMessage = 'Email cannot contain spaces';
      }
      else {
        this.emailMessage = "";
        this.validEmail = true;
      }

      this.validPassword = false;
      if (this.password.length < 6) {
        this.passwordMessage = "Password should be minimum 6 characters";
      }
      else if (this.password.indexOf(' ') >= 0) {
        this.passwordMessage = "Password cannot contain spaces";
      }
      else {
        this.passwordMessage = '';
        this.validPassword = true;
      }


      if (this.validEmail && this.validPassword) {
        this.email = "";
        this.password = "";
        this.validEmail = false;
        this.validPassword = false;
      }
      else {
        alert(this.emailMessage + '\n' + this.passwordMessage);
      }
    }
  }
}
</script>
<template>
  <form @submit.prevent="onSubmit">
    <div class="mb-3">
      <label for="exampleInputEmail1" class="form-label">Email address</label>
      <input v-model="email" type="email" class="form-control">
    </div>
    <div v-if="emailMessage.length > 0" class="alert alert-danger" role="alert">
      {{  emailMessage }}
    </div>
    <div class="mb-3">
      <label for="exampleInputPassword1" class="form-label">Password</label>
      <input v-model="password" type="password" class="form-control">
    </div>
    <div v-if="passwordMessage.length > 0" class="alert alert-danger" role="alert">
      {{  passwordMessage }}
    </div>
    <button type="submit" class="btn btn-primary">Submit</button>
  </form>
  <br>
  <div class="card">
    <div class="card-body">
      Email: {{ email }}
      <br>
      Password: {{ password }}
    </div>
  </div>
</template>