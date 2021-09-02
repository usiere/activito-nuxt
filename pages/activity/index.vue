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
            <h1>
                {{jokes.activity}}
            </h1>
            <h1>
                {{jokes.key}}
            </h1>
            <h1>
                {{jokes.participants}}
            </h1>
            <h1>
                {{jokes.price}}
            </h1>
             <button @click="loadActivity()" class="load-button">Suggest activiy </button>
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
}

.load-button:hover{
    color: white;
    background-color: black;
}

.anim-grid{
    display: grid;
    grid-template-columns: 50% 50%;
}

@keyframes anim1 {
	0% {
        position: relative;
		left: 50px;
	}
	100% {
        position: relative;
		right: 0px;
	}
}

.anim-grid1{
    width: 100px;
    height: 100px;
    background-color: darkcyan;
    border-radius: 40%;
    animation: anim1 4s ease-in-out;
}

.anim-grid2{
    width: 100px;
    height: 100px;
    background-color: pink;
    border-radius: 40%;
    animation: anim1 infinite ease-in;
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