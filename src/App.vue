<template>
  <div id="app">

    <b-container class="control">
      <b-row>
        <b-col class="red">
          <div class="input-button">
            <input placeholder="Add new user" type="text" v-model="newuser"><span><b-button  @click="addNewUser" >ADD USER</b-button></span>
          </div>
        </b-col>
        <b-col class="blue">
          <div class="unordered-list">
            <ul class="list-group listings">
            <b-list-group-item href="#" variant="secondary">List of Users</b-list-group-item>
             <li class="list-group-item" v-for="(user, index) in users" :key="index">{{user.name}}
            <b-button variant="danger" @click="deleteUser(user)">REMOVE</b-button></li>
        </ul>
          </div>
          
      </b-col>
   
  </b-row>


    </b-container>

    
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',
  components: {},
  data(){
    return {
      users: [],
     newuser: null,
      userSelected: false
    }
  },
    methods: {
      addNewUser(){
      this.users.push({name: this.newuser});
      this.newuser = ""
      console.log(this.newuser)
      },
      deleteUser(user){
        this.userSelected = this.users.indexOf(user);
        this.users.splice(this.userSelected, 1)
      }
      
    },
    async created(){
        //Get all users by making a get request to /users
        let fetchUsers = await axios.get("https://jsonplaceholder.typicode.com/users");
       console.log(fetchUsers);
       this.users = fetchUsers.data;
  }
}
</script>

<style scoped>
.input-button{
  margin-top: 4em ;
  margin-left: 1em;
}
.delete-button{
  float: right;
  color: rgb(252, 7, 7);
  width: 10%;
  text-align: center;
  border-radius: 50%;
  font-weight: bolder;
  background-color: black;
}
.listings:hover{
  cursor: pointer;
}
.unordered-list{
  margin-top: 50px;
}
.control{
  width: 50%;
  
  box-shadow: 0 15px 30px rgba(90, 110, 100, 0.7);
}
</style>

<script>
import axios from 'axios'
export default {
  name: 'App',
  components: {},
  data(){
    return {
      users: [],
      newuser: null,
      userSelected: false
    }
  },
    methods: {
      addNewUser(){
      this.users.push({name: this.newuser});
      this.newuser = ""
      console.log(this.newuser)
      },
      deleteUser(user){
        this.userSelected = this.users.indexOf(user);
        this.users.splice(this.userSelected, 1)
      }
      
    },
    async created(){
        //Get all users by making a get request to /users
        let fetchUsers = await axios.get("https://jsonplaceholder.typicode.com/users");
       console.log(fetchUsers);
       this.users = fetchUsers.data;
  }
}
</script>

<style scoped>
.input-button{
  margin-top: 4em ;
  margin-left: 1em;
}
.delete-button{
  float: right;
  color: rgb(252, 7, 7);
  width: 10%;
  text-align: center;
  border-radius: 50%;
  font-weight: bolder;
  background-color: black;
}
.listings:hover{
  cursor: pointer;
}
.unordered-list{
  margin-top: 50px;
}
.control{
  width: 50%;
  
  box-shadow: 0 15px 30px rgba(90, 110, 100, 0.7);
}
</style>
