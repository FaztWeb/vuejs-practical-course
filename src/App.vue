<template>
  <div id="app">
    <nav>
      <ul>
        <li>
          <router-link to="/">
            users
          </router-link>
        </li>
        <li>
          <router-link to="/test">
            Test
          </router-link>
        </li>
      </ul>
    </nav>
    <img src="./assets/logo.png">
    <!-- <Test msg="Hello"/> -->
    <!-- <users></users> -->
    <router-view></router-view>
  </div>
</template>

<script>
import Test from './components/Test';
import Users from './components/User';

export default {
  name: 'app',
  components: {
    Test,
    Users
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
