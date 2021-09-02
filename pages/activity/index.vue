<template>
    <div class="main">
        <!-- there will be three sections that will be divided here -->
        <!-- Animation zone -->
        <div class="anim-grid">
            <div class="anim-grid1"></div>
            <div class="anim-grid2"></div>
        </div>

        <!-- section 2  -->
        <div class="sec1" v-show="showSec1">
                <h1>
                Ask our Activito genie to get more activity ideas
        </h1>
        <button @click="loadActivity(), changeSec()" class="load-button">Suggest activiy </button>
        </div>


        <!-- section 3 -->
        <div class="sec2" v-show="showSec2">        
             <h1>Your activity for today is to ....</h1>
             <div class="activity-container">
                     <h1>
                {{jokes.activity}}
            </h1>
             </div>
        
            <!-- <h1>
                {{jokes.key}}
            </h1>
            <h1>
                {{jokes.participants}}
            </h1>
            <h1>
                {{jokes.price}}
            </h1> -->
             <button @click="loadActivity()" class="load-button">Suggest another </button>
            </div>
   
    </div>
</template>


<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans:wght@200&display=swap');

.main{
    margin-top: 300px;
    margin-left: 20%;
    display: flex;
    flex-direction: column;
    font-family: 'Josefin Sans', sans-serif;
}

.load-button{
    width: 100px;
    height: 40px;
    background-color: white;
    color: black;
    cursor: pointer;
    border-radius: 10px;
    margin: 20px;
    position: relative;
    left: 300px;
}

.load-button:hover{
    color: white;
    background-color: black;
}

.anim-grid{
    display: grid;
    grid-template-columns: 50% 50%;
}

.activity-container{
    width: 700px;
    height: 60px;
    border: 1px solid black;
    padding: 20px;
    border-radius: 10px;
}
@keyframes anim1 {
  0% { opacity: 20%; margin-top: 40px; border-radius: 30%;}
  20% { opacity: 60%; margin-top: 20px; border-radius: 50%;}
  30% { opacity: 100%; margin-top: 50px; border-radius: 70%;}
  60% { margin-top: 30px; border-radius: 90%;}
  100% {margin-top: 0px; border-radius: 30%;}
}


.anim-grid1{
    width: 100px;
    height: 100px;
    background-color: darkcyan;
    border-radius: 40%;
    animation-name: anim1;
  animation-duration: 3s;
  animation-iteration-count: infinite;
  animation-timing-function: ease-in-out;
}

.anim-grid2{
    width: 100px;
    height: 100px;
    background-color: pink;
    border-radius: 40%;
    animation-name: anim1;
  animation-duration: 3s;
  animation-iteration-count: infinite;
  animation-timing-function: ease-in-out;
}





</style>

<script>
import axios from "axios";

export default {

    data(){
        return {
            jokes: [],
            showSec1: true,
            showSec2: false

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
        },

        // method to change the view of Sec1 and Sec2
        async changeSec(){
            this.showSec1 =  !this.showSec1,
            this.showSec2 =  !this.showSec2
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