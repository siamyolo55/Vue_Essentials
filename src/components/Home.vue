<template>
    <Header/>
    <h1> Hello {{name}} </h1>
    <table border="1">
        <tr>
            <td>Id</td>
            <td>Name</td>
            <td>Contact</td>
            <td>Address</td>
        </tr>
        <tr v-for="item in restaurants" :key="item.id">
            <td>{{item.id}}</td>
            <td>{{item.name}}</td>
            <td>{{item.contact}}</td>
            <td>{{item.address}}</td>
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

        components:{
            Header
        },

        async mounted(){
            let info = localStorage.getItem('user-info')
            this.name = JSON.parse(info).name
            if(!info){
                this.$router.push({name : "SignUp"})
            }   
            let result = await axios.get("http://localhost:3000/restaurants")
            this.restaurants = result.data

        }
    }
</script>

<style >
    td{
        width: 160px;
        height: 40px;
    }
</style>