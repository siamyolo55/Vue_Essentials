<template>
    <Header/>
    <h1> Add restaurant page </h1>
    <form class="add">
        <input type="text" name="name" placeholder="Enter Name" v-model="restaurant.name"/>
        <input type="text" name="address" placeholder="Enter Address" v-model="restaurant.address"/>
        <input type="text" name="contact" placeholder="Enter Contact" v-model="restaurant.contact"/>
        <button type="button" v-on:click="addRestaurant">Add new restaurant</button>
    </form>
</template>


<script>
    import Header from './Header.vue'
    import axios from 'axios'
    export default{
        name : "Add",

        data(){
            return{
                restaurant:{
                    name : '',
                    address : '',
                    contact : ''
                }
            }
        },

        methods:{
            async addRestaurant(){
                let result = await axios.post("http://localhost:3000/restaurants",{
                    name : this.restaurant.name,
                    address : this.restaurant.address,
                    contact : this.restaurant.contact
                })
                console.log(result)
                if(result.status == 201){
                    this.$router.push({name : "Home"})
                }
            }
        },
        
        components:{
            Header
        },

        mounted(){
            let info = localStorage.getItem('user-info')
            if(!info){
                this.$router.push({name : "SignUp"})
            }
        }
    }
</script>