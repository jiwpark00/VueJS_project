<script>
export default {
  data() {
    return {
      users: [],
      searchTerm: 'greg',
      isLoading: false
    }
  },
  methods: {
    async fetchGitHubUsers() {
      const res = await fetch(`https://api.github.com/search/users?q=${this.searchTerm}`);
      const data = await res.json();
      this.isLoading = false;
      return data.items
    },
  },
  async created() {
    this.users = await this.fetchGitHubUsers();
  },
  async onSubmit(e) {
    console.log("AYE!");
    this.isLoading = true;
    this.users = await this.fetchGitHubUsers();
  }
}
</script>
<template>
  <form @submit.prevent="onSubmit">
    <div class="mb-3">
      <input v-model="searchTerm" type="text" class="form-control">
    </div>
    <button type="submit" class="btn btn-primary">Submit</button>
  </form>
  <div v-if="isLoading" class="spinner-border" role="status">
  </div>
  <table class="table">
    <thead>
      <tr>
        <th scope="col">Id</th>
        <th scope="col">Avatar</th>
        <th scope="col">Login</th>
        <th scope="col">URL</th>
      </tr>
    </thead>
    <tbody>
      <tr :key="user.id" v-for="user in users">
        <th scope="row">{{ user.id }}</th>
        <td><img :alt='user.login' :src='user.avatar_url' width="75" height="75" /></td>
        <td>{{ user.login }}</td>
        <td><a :href="user.html_url">{{ user.html_url }}</a></td>
      </tr>
    </tbody>
  </table>
</template>