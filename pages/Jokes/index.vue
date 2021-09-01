<template>
    <div>
        <!-- there will be three sections that will be divided here -->

        <!-- section 1 -->
        <div>
            Welcome to the activity predictor, where we magically suggest activities for you.
            <button>Get started</button>
        </div>


        <!-- section 2  -->
        <div>
                <h1>
            checking here for differences  <br>
            click here to get more activities.
            <button @click="loadActivity()" class="load-button">Suggest activiy </button>
        </h1>
        </div>


        <!-- section 3 -->
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
    </div>
</template>


<style scoped>

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