<template>
  <div id="app" class="container">
    <h1>peopol</h1>
    <hr>
      <div class="input-group d-flex">
        <button v-if="addShow2" class="btn btn-success" v-on:click="addShow()">Add</button>
        <button v-else class="btn btn-success" v-on:click="addHide()">X</button>
        <input class="form-control" placeholder="Search" aria-label="Search" v-model="searchName"
        v-on:keyup="srchNAME(searchName)">
        <button v-if="searched" class="btn btn-primary" v-on:click="srchNAME(searchName)">Search</button>
        <button v-else class="btn btn-secondary" v-on:click="srchCLR()">Clear</button>
      </div>
    <hr>
    <div  v-bind:class="{ 'd-none': isActive }">
      <div class="input-group d-flex flex-row">
        <input v-model="name2" type="text" class="form-control" placeholder="Name....">
        <input v-model="username2" type="text" class="form-control" placeholder="Username....">
        <input v-model="email2" type="text" class="form-control" placeholder="Email....">
        <input v-model="website2" type="text" class="form-control" placeholder="Website....">
        <button v-on:click="add()" class="btn btn-primary">Add</button>
      </div>
      <hr>
    </div>
    <div v-if="formErr" class="alert alert-danger">
      Fill in Name!
    </div>
    <div class="row">
      <profile v-for="person in peopleArr" :key="person.id" v-bind:person="person"
      v-on:personDel="person_del"/>
    </div>
    <button v-on:click="getUsers()" class="btn btn-primary">Get</button>
  </div>
</template>

<script>
import Profile from './components/profile.vue'
export default {
  name: 'App',
  components: {
    Profile
  },
  data () {
    return {
      peopleArr: [],
      peopleArrOrg: [],
      idNum: null,
      name2: null,
      username2: null,
      email2: null,
      website2: null,
      formErr:false,
      searchName: null,
      searched: true,
      addShow2:true,
      isActive: true      
    }
  },
  mounted () {
    this.getProfiles()

  },
  methods: {
    async getProfiles(){
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/users')
        const data = await response.json()
        //this.employees = data
        console.log(data)
        this.peopleArr = data
        this.peopleArrOrg = data
        this.idNum = this.peopleArr.length+1
      } catch (error) {
        console.error(error)
      }
    },
    person_del(id) {
      this.peopleArr = this.peopleArr.filter((person) => {
        return person.id != id;
      });
      this.peopleArrOrg = this.peopleArrOrg.filter((person) => {
        return person.id != id;
      });
    },
    add() {
      if(this.name2 == null || this.name2 == ''){
        this.formErr = true;
        return
      }
      let newPerson = {
        id: this.idNum,
        name: this.name2,
        username: this.username2,
        email: this.email2,
        website: this.website2
      }
      this.peopleArr.push(newPerson)
      this.peopleArrOrg = this.peopleArr
      this.name2 = null
      this.username2 = null
      this.email2 = null
      this.website2 = null
      this.idNum++
      this.formErr = false
      this.isActive = true
      this.addShow2 = true
    },
    srchNAME(name) {
      this.peopleArr = this.peopleArrOrg

      if(name.length < 1 || name == null) {
        this.searched = true
        return
      }

      this.peopleArr = this.peopleArr.filter((person) => {
        return person.name.toLowerCase().includes(name);
      })
      this.searched = false
    },
    srchCLR() {
      this.peopleArr = this.peopleArrOrg
      this.searched = true
      this.searchName = null
    },
    addShow() {
      this.isActive = false
      this.addShow2 = false
    },
    addHide() {
      this.isActive = true
      this.addShow2 = true
    },
    async getUsers(){
      try {
        const response = await fetch('http://127.0.0.1:3000/users2')
        const data = await response.json()
        const data2 = data[0]
        //this.employees = data[0]
        console.log(data2)

        data2.forEach(person => {
          this.peopleArr.push(person)
        });
        
        //this.peopleArrOrg = this.peopleArr
  
        // this.peopleArr = data
        // this.idNum = this.peopleArr.length+1
      } catch (error) {
        console.error(error)
      }
    }
  }
}
</script>

<style>
</style>