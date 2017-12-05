<template lang="html">
  <div class="users">
    <h1>User component</h1>
    <ul>
      <li v-for="user in users">
        <input type="checkbox" v-model="user.contacted">
        <span :class="{contacted: user.contacted}">
          {{user.name}} - {{user.email}} <button @click="deleteUser(user)">X</button>
        </span>
      </li>
    </ul>
    <form v-on:submit.prevent="addUser">
      <input type="text" v-model="newUser.name" placeholder="Name" autofocus>
      <input type="email" v-model="newUser.email" placeholder="email">
      <button type="submit">
        Add user
      </button>
    </form>

    <hr>
  </div>
</template>

<script>
  export default {
  name: 'users',
  data() {
    return {
      users: [
        {
          name: 'joe',
          email: 'joe@mail.com',
          contacted: false
        },
        {
          name: 'ryan',
          email: 'ryan@mail.com',
          contacted: false
        },
        {
          name: 'donna',
          email: 'donna@mail.com',
          contacted: true
        }
      ],
      newUser: {},
    }
  },
  methods: {
    addUser() {
      this.users.push(this.newUser)
      // this.newUser = {}
    },
    deleteUser(user) {
      this.users.splice(this.users.indexOf(user), 1);
    }
  },
  created() {
    this.$http.get('https://jsonplaceholder.typicode.com/users')
    .then(res => this.users = res.data)
  }
}
</script>

<style lang="css">
  ul li {
    text-align: left;
  }
  .contacted {
    text-decoration: line-through;
  }
</style>
