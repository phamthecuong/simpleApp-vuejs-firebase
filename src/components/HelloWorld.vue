<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{dataName}}</h2>
    <router-link to="/News">News</router-link>
  </div>
</template>

<script>
  
  // var config = {
  //   apiKey: "AIzaSyBK0MvfrMXRHi-ed0rhGfHmZkajJ4DYCZA",
  //   authDomain: "todolistwithvuejs.firebaseapp.com",
  //   databaseURL: "https://todolistwithvuejs.firebaseio.com",
  //   projectId: "todolistwithvuejs",
  //   storageBucket: "todolistwithvuejs.appspot.com",
  //   messagingSenderId: "267452762324"
  // };
  // firebase.initializeApp(config);

export default {
  name: 'HelloWorld',
  data () {
    return {
      dataName: 'pham the cuong',
      msg: 'This is my first app from vuecli'
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
