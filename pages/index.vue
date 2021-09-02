<template>

<div>
  <div class="topbar">
    <h1>Activito</h1>
    <h6>help?</h6>
  </div>

  <div class="main">
  <div class="grid-left">
     <h1 class="main-text">Welcome to activity genie</h1>
  <span class="sub-text">This is where we predict activities for you</span> 
  <br><br>
  <NuxtLink to="/activity" class="main-btn">Get started</NuxtLink>
  
  </div>
  <div class="grid-right">
    <img src="../assets/illus-home.png" alt="" width="500px">
  </div>
 
</div>

</div>



</template>


<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans:wght@200&display=swap');

.topbar{
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  margin-left: 20px;
  margin-right: 20px;
}

.main{
  padding: 180px;
  display: grid;
  grid-template-columns: 50% 50%;
}

.main-text{
  font-size: 40px;
  font-family: 'Josefin Sans', sans-serif;
}

.sub-text{
  font-size: 15px;
  font-family: 'Josefin Sans', sans-serif;
}

.main-btn{
  background-color: white;
  color: black;
  border-radius: 30px;
  padding: 10px;
  cursor: pointer;
  border: 1px solid black;
  outline: none;
  text-decoration: none;
}

.main-btn:hover{
   background-color: #6C63FF;
  color: white;
  border: 1px solid black;
}


</style>

<script>
import axios from "axios";

export default {

    data(){
        return {
            jokes: []
        }
    },

//     async created(){
//         const config = {
//             headers: {
//                 'Accept' : 'application/json'
//             }
//         }
//    try {
//       const res = await axios.get("https://www.boredapi.com/api/activity", config);
//       this.jokes = res.data;
//       console.log(this.jokes)
//     } catch (err) {
//       console.log(err);
//     }

//     },

    methods: {
        async loadActivity(){
                    const config = {
            headers: {
                'Accept' : 'application/json'
            }
        }
   try {
      const res = await axios.get("https://www.boredapi.com/api/activity", config);
      this.jokes = res.data;
      console.log(this.jokes)
    } catch (err) {
      console.log(err);
    }
        }
    },

    head() {
        return {
            title: 'Dad jokes',
            meta: [
                {
                    hid: "description",
                    name: "description",
                    content: "This is where we suggest activities to you"
                }
            ]
        }
    }
    
}
</script>