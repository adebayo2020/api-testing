<template>
    <div >
        <p id="users-welcome">This the users page</p> <hr>

        <div id="form-box">
            <b-form inline>
                <div id="input-form">
                <b-input
                  id="inline-form-input-name"
                  class="mb-2 mr-sm-2 mb-sm-0"
                  placeholder="Enter a name"
                  type="text"
                  v-model="name"
                ></b-input>
                </div>

                <b-button id="add-btn-color"  @click="addName">Add</b-button>
            </b-form>
            <hr>

            <div id="form-list">
                <ul class="list-group">

                    <li class="list-group-item" id="custom" v-for="user in users" :key="user.id">
                        {{user.name}}
                        <span id="custom-btn"  @click="deleteName">X</span>
                    </li> 
                </ul>
            
            </div>
            <hr>
        </div>

        

       
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data(){
        return{
            users: [],
            name: ""
        }
    },
    async created(){
        let fetchUsers = await axios.get(
            'https://jsonplaceholder.typicode.com/users'
        );
        // console.log(fetchUsers);

        this.users = fetchUsers.data;
    },
    methods:{
        addName(){
            if(this.name===""){
                alert('Invalid!!! Enter a name please')
            }else{
                   let id = this.users.length + 1
                    let user = { id: id, name: this.name }
                    this.users.push(user)
                    this.name = ""
            }
        },

        deleteName(name){
              let currentName = this.users.indexOf(name)
              this.users.splice(currentName, 1)
        }
    }
}
</script>

<style scoped>
#custom{
    height: 40px;
    width: 300px;
    background-color: rebeccapurple;
    color: whitesmoke;
}
#custom-btn{
    color: tomato;
    cursor: pointer;
    float: right;

}
#users-welcome{
    text-align: center;
}
#form-box{
    margin-left: 300px;
    background-color: whitesmoke;
    width:770px;
    min-height: 3px;
}
#input-form{
    margin-left: 240px;
}
#form-list{
    margin-left: 224px;
}
#add-btn-color{
    background-color: rebeccapurple;
}
</style>
