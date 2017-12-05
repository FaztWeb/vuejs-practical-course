<template lang="html">
  <div class="test">
    <h1>{{title}}</h1>
    <p>{{user.firstName}}</p>
    <p v-text="user.lastName"></p>
    <p v-html="user.titleHTML"></p>

    <hr>
    <p v-if="showName">
      {{user.firstName}}
    </p>
    <p v-else="showName">Not Allowed</p>

    <hr>
    <ul>
      <li v-for="task in tasks">
        {{task.title}}
      </li>
    </ul>

    <hr>
    <input type="text" v-model="title" placeholder="Write a Title">

    <hr>
    <button type="button" v-on:click="greet('ryan')">
      Click Me!
    </button> <br>
    <button type="button" v-on:click="greetAPerson(user.firstName)">
      Click Me!
    </button> <br>
    <input type="text" v-on:keyup="pressKey" v-on:keyup.enter="enterHit">

    <hr>
    <input type="text" v-model="user.firstName" placeholder="First Name">
    <input type="text" v-model="user.lastName" placeholder="last Name">
    {{fullName}}

    <hr>
    <h3>{{msg}}</h3>
  </div>
</template>

<script>
export default {
  name: 'test',
  data() {
    return {
      title: 'Hello World',
      user: {
        firstName: 'joe',
        lastName: 'macmillan'
      },
      titleHTML: '<h1>Hello World</h1>',
      showName: true,
      tasks: [
        {title: 'eat'},
        {title: 'run'},
        {title: 'dinner'},
        {title: 'do work'}
      ]
    }
  },
  methods: {
    greet(name) {
      alert('hello ' + name);
    },
    greetAPerson(name) {
      alert('hello ' + name);
    },
    pressKey(e) {
      // console.log('you pressed', e.key);
      console.log('you pressed', e.target.value);
    },
    enterHit(){
      console.log('you hit enter');
    }
  },
  computed: {
    fullName(){
      return this.user.firstName + ' ' +  this.user.lastName
    }
  },
  props: {
    msg: {
      type: String,
      default: 'FooBar'
    }
  }
}
</script>

<style lang="css">
  ul li {
    text-align: left;
  }
</style>
