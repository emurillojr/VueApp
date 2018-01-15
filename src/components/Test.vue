<template>
  <div class="test">
    <input type="text" v-model="title">
    <br />
    <h1>{{title}}</h1>
    <p v-if="showName">{{user.firstName}}</p>
    <p v-else>Nobody</p>
    <!-- <p v-text="user.firstName"></p> -->
    <ul>
      <li v-for="item in items">{{item.title}}</li>
    </ul>
    <button v-on:click="greet">Say Greeting</button>
    <!-- <button v-on:click="greet('Hello World')">Say Greeting</button>  another way*-->
    <br />
    <input type="text" v-on:keyup="pressKey" v-on:keyup.enter="enterHit">
    <hr />

    <label>First Name: </label><input type="text" v-model="user.firstName">
    <br />
    <label>Last Name: </label><input type="text" v-model="user.lastName">
    <br />
    <h3>{{fullName}}</h3>
    <br />
    <h2>{{msg}}</h2>
  </div>
</template>

<script>
  export default {
    name: 'test',
    props: {
      msg: {
        type: String,
        default:'Foobar'
      }
    },
    data() {
      return {
        title: 'Hello World',
        user: {
          firstName: 'John',
          lastName: 'Doe'
        },
        showName: true, //true = john  false = nobody
        items: [
          {title: 'Item One'},
          {title: 'Item Two'},
          {title: 'Item Three'}
        ]
      }
    },
    methods: {
      greet: function () {
        alert('Hello');
      },
      pressKey: function (e) {
        console.log(e.target.value)
      },
      enterHit: function () {
        console.log('You hit enter')
      }
      },
      //computed property for the full name that will take both and add them together and also update if one is updated
      computed: {
        fullName: function(){
          return this.user.firstName+ ' ' +this.user.lastName;
        }
      } 
    }
  

</script>

<style scoped>


</style>
