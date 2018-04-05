<template>
  <div id="app">
    <!-- <img src="./assets/logo.png">
    <router-view/> -->
      <div class="container">
        <h2 class="title-app">App simple vuejs with firebase</h2>
        <div></div>
        <form class="form-inline" >
          <div class="form-group">
            <label for="email">Title:</label>
            <input type="text" v-model="newBook.title" class="form-control" id="email" placeholder="Enter Title" name="email">
          </div>
          <div class="form-group">
            <label for="pwd">Author:</label>
            <input type="text" v-model="newBook.author" class="form-control" id="pwd" placeholder="Enter author" name="pwd">
          </div>
          <div class="form-group">
            <label for="email">Link book:</label>
            <input type="text"  v-model="newBook.url" class="form-control" id="email" placeholder="Enter Link book" name="email">
          </div>
        
          <button v-on:click="addBook()" type="submit" class="btn btn-primary">Submit</button>
        </form>
      </div>
      <hr>
      
    <div class="container">
      <h2>List books</h2>
      <table class="table">
        <thead>
          <tr>
            <th>Title</th>
            <th>Author</th>
            <th>Url</th>
            <th >Action</th>
          </tr>
        </thead>
        <tbody>
          <tr class="info" v-for="book in books">
            <td>{{book.title}}</td>
            <td>{{book.author}}</td>
            <td>{{book.url}}</td>
            <td>
              <span class="glyphicon glyphicon-pencil"></span>
              <span v-on:click="deleteItem(book)" class="glyphicon glyphicon-trash"></span>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
      
  </div>
</template>



<script>
import Firebase from 'firebase';
let config = {
    apiKey: "AIzaSyBK0MvfrMXRHi-ed0rhGfHmZkajJ4DYCZA",
    authDomain: "todolistwithvuejs.firebaseapp.com",
    databaseURL: "https://todolistwithvuejs.firebaseio.com",
    projectId: "todolistwithvuejs",
    storageBucket: "todolistwithvuejs.appspot.com",
    messagingSenderId: "267452762324"
  };
let app = Firebase.initializeApp(config);
let db = app.database();
let booksRef = db.ref('books');
export default {
  name: 'App',
  firebase: {
    books: booksRef
  },
  data () {
    return {
      newBook: {
        title: '',
        author: '',
        url: ''
      }
    }
  },
  methods: {
    addBook: function() {
      booksRef.push(this.newBook);
      this.newBook.title = '';
      this.newBook.author = '';
      this.newBook.url = '';
    },
    deleteItem: function(book) {
      booksRef.child(book['.key']).remove();
      console.log("boook", book);
    },
    updateItem: function(book) {
      booksRef.child(book['.key']).update();
    }
  }
}
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #0d2b49;
    margin-top: 60px;
  }
  .table thead tr th {
      text-align: center;
    }
    .title-app {
      padding-bottom: 32px;
      color: chocolate;
    }
</style>

