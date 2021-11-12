<template>
  <div >
    <h1>Home Page</h1>
    <h1>your name is {{name}}</h1>
    <h1>your email is {{email}}</h1>
    <button @click="logout">logout</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Home',
  created(){
    if(localStorage.getItem("token") == null){
      this.$router.push("/login")
    }
  },
  mounted(){
    axios.get("http://localhost:5000/users",{headers:{token:localStorage.getItem("token")} })
         .then((res)=>{
           this.email = res.data.user.email
           this.name = res.data.user.name
      })
      .catch((err)=>{
        console.log(err)
      })
 },
  data(){
    return{
      email:'',
      name:''
    }
  },
  methods:{
    logout(){
      localStorage.clear()
      this.$router.push("/login")
    }
  },
  components: {

  }
}
</script>
