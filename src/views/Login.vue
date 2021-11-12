<template>
  <div class="container-fluid">
    <div class="row">
        <div class="col-sm-3 "> </div>
        <div class="col-sm-6">
            
            <form @submit.prevent="login">
                <div class="mb-3 mt-3">
                    <label for="email" class="form-label">Email:</label>
                    <input type="email" v-model="formData.email" class="form-control" id="email" placeholder="Enter email" name="email">
                </div>
                <div class="mb-3">
                    <label for="pwd" class="form-label">Password:</label>
                    <input type="password" v-model="formData.password" class="form-control" id="pwd" placeholder="Enter password" name="pswd">
                </div>
                <button type="submit" class="btn btn-primary">Submit</button>
                {{error}}
            </form>

        </div>
        <div class="col-sm-3"> </div>
    </div>
</div>
</template>

<script>
import axios from  'axios'
export default {
  name: 'Login',
  data(){
    return{
      formData:{
        email:'',
        password:'',
        error:''
      }
    }
  },
  onupdate(){
    this.error
  },
  methods:{
    login(){
      axios.post("http://localhost:5000/auth/login",this.formData)
           .then((res)=>{
             if(res.status == 200){
                localStorage.setItem("token",res.data.token)
                console.log(res.data.token)
                this.$router.push("/")
             }
           })
           .catch((err)=>{
             console.log(err.response.data.error)
             this.error = err.response.data.error
           })
    }
  },
  components: {

  }
}
</script>
