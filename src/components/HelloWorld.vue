<template>
<div class="row">
        <div class="col s12 m6">
          <div class="card blue-grey darken-1">
            <div class="card-content white-text">
              <span class="card-title">Telegram Bot</span>
              <label>Telegram Token</label>
              <input id="teletoken" v-model="teletoken">
              <label>Chatid</label><input id="chatid">
              <label>Prefix</label><input id="prefix">
              <label>Id message start</label><input id="idmsgstart">
            </div>
            <div class="card-action">
              <a class="waves-effect waves-light btn" v-on:click="clickHandle">Get News</a>
              <a class="waves-effect waves-light btn">Post News</a>
            </div>
          </div>
        </div>
        <div class="col s12 m6">
          <div class="card blue-grey darken-1">
            <div class="card-content white-text">
              <span class="card-title">Bot Info</span>
              <label>IdBot</label>
              <label>Name</label>
              <label>UserName</label>
            </div>
          </div>
        </div>
      </div>        
</template>

<script>
var axios = require('axios');
export default {
  name: 'HelloWorld',
  data () {

    return {
      msg: 'Welcome to Your Vue.js App',
      teletoken:''
    }
  }, 
  methods: {
    clickHandle: function(event) {
      axios.get("https://api.telegram.org/bot" + this.teletoken + "/getUpdates")
    .then(function (response) {
        console.log(response);
    })
    .catch(function (error) {
        console.log(error.message);
    });   
    }
  },
  watch: {
    teletoken: function(val, Oldval) {
      console.log(this.teletoken)
      axios.get("https://api.telegram.org/bot" + this.teletoken + "/getMe")
    .then(function (response) {
        console.log(response);
    })
    .catch(function (error) {
        console.log(error.message);
    });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
