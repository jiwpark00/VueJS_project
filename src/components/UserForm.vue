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
      if (this.validEmail) {
        alert('Email:' + this.email + '\nPassword:' + this.password);
      }
      else {
        console.log(this.emailMessage);
        alert(this.emailMessage);
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
    <div class="mb-3">
      <label for="exampleInputPassword1" class="form-label">Password</label>
      <input v-model="password" type="password" class="form-control">
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