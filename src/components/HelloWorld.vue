<template>
    <div class="container">
      <div class="input-group mb-3">
        <span class="input-group-text" id="basic-addon1">@</span>
        <input v-model="data.login" type="text" class="form-control" placeholder="Username" aria-label="Username" aria-describedby="basic-addon1">
      </div>

      <div class="input-group mb-3">
        <span class="input-group-text" id="basic-addon1">@</span>
        <input v-model="data.password" type="text" class="form-control" placeholder="Username" aria-label="Username" aria-describedby="basic-addon1">
      </div>

      <button class="btn btn-info" @click="sendRequest">
        click me
      </button>
    </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
      data:{
        login:null,
        password:null
      }
    }
  },
  methods:{
    async sendRequest(){
      const body = {
        login: this.data.login,
        password: this.data.password
      }

      this.data =await axios.post('http://127.0.0.1:3000/user/create', body, {
        headers: {
          'Access-Control-Allow-Origin': '*'
        },
      }) 
      console.log(this.data)


    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
