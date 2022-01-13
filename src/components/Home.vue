<template>
    <Header/>
    <h1>List of Restaurants</h1>
    <table border="1">
        <tr>
            <td>Id</td>
            <td>Name</td>
            <td>Contact</td>
            <td>Address</td>
            <td>Action</td>
        </tr>
        <tr v-for="item in restaurants" :key="item.id">
            <td>{{item.id}}</td>
            <td>{{item.name}}</td>
            <td>{{item.contact}}</td>
            <td>{{item.address}}</td>
            <td>
                <router-link :to="'/update/'+ item.id">Update</router-link><br>
                <button v-on:click="deleteRestaurant(item.id)">Delete</button>
            </td>
        </tr>
    </table>
</template>


<script>
    import Header from './Header.vue'
    import axios from 'axios'
    export default{
        name : "Home",

        data(){
            return{
                name : '',
                restaurants: []
            }
        },

        methods:{

            async deleteRestaurant(id){
                let result = await axios.delete("http://localhost:3000/restaurants/"+id)
                console.log(result) 
                let upp = await axios.get("http://localhost:3000/restaurants")
                this.restaurants = upp.data
            },

            async loadData(){
                let info = localStorage.getItem('user-info')
                if(!info){
                    this.$router.push({name : "SignUp"})
                } 
                this.name = JSON.parse(info).name
                console.log('Reached here')  
                let result = await axios.get("http://localhost:3000/restaurants")
                this.restaurants = result.data
            }
        },

        components:{
            Header
        },

        async mounted(){
            this.loadData()
        }
    }
</script>

<style >
    td{
        width: 160px;
        height: 40px;
    }
</style>