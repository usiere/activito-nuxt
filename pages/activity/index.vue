<template>
    <div class="main">
        <!-- there will be three sections that will be divided here -->
Animation zone
        <div class="anim-grid">
            <div class="anim-grid1"></div>
            <div class="anim-grid2"></div>
        </div>

        <!-- section 2  -->
        <div>
                <h1>
                Ask our Activito genie to get more activity ideas
        </h1>
        <button @click="loadActivity()" class="load-button">Suggest activiy </button>
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

.main{
    margin-left: 20%;
    display: flex;
    flex-direction: column;
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

.anim-grid1{
    width: 100px;
    height: 100px;
    background-color: darkcyan;
    border-radius: 40%;
}

.anim-grid2{
    width: 100px;
    height: 100px;
    background-color: pink;
    border-radius: 40%;
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