<template>
  <div class="container-fluid">
    <div class="row">
        <div class="col-sm-3 "> </div>
        <div class="col-sm-6">
            
            <form @submit.prevent="signup">
                <div class="mb-3 mt-3">
                    <label for="name" class="form-label">Name:</label>
                    <input type="text" v-model="formData.name" class="form-control" id="name" placeholder="Enter Name" name="name">
                </div>
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
import axios from 'axios'
export default {
  name: 'Signup',
  data(){
      return{
          formData:{
              name:'',
              email:'',
              password:'',
              error:''
          }
      }
  },
  methods:{
      signup(){
        console.log(this.formData)
        axios.post("http://localhost:5000/auth/signup",this.formData)
             .then((res)=>{
                 console.log(res.data)
                 this.$router.push('/Login')
             })
             .catch((err)=>{
                 console.log(err.data)
                 this.error = err.response.data.error
             })
      }
  },
  components: {

  }
}
</script>
