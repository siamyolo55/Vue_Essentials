<template>
    <Header/>
    <h1> Update restaurant page</h1>
    <form class="add">
        <input type="text" name="name" placeholder="Enter Name" v-model="restaurant.name"/>
        <input type="text" name="address" placeholder="Enter Address" v-model="restaurant.address"/>
        <input type="text" name="contact" placeholder="Enter Contact" v-model="restaurant.contact"/>
        <button type="button" v-on:click="updateRestaurant">Update restaurant</button>
    </form>
</template>


<script>
    import Header from './Header.vue'
    import axios from 'axios'
    export default{
        name : "Update",

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
            async updateRestaurant(){
                let result = await axios.put('http://localhost:3000/restaurants/'+this.$route.params.id,{
                    name : this.restaurant.name,
                    address : this.restaurant.address,
                    contact : this.restaurant.contact
                })
                console.log(result)
                this.$router.push({name:"Home"})
            }
        },
        
        components:{
            Header
        },

        async mounted(){
            let info = localStorage.getItem('user-info')
            if(!info){
                this.$router.push({name : "SignUp"})
            }
            let result = await axios.get('http://localhost:3000/restaurants/'+this.$route.params.id)
            this.restaurant = result.data
        }
    }
</script>