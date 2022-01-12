<template>
    <Header/>
    <h1> Add restaurant page </h1>
</template>


<script>
    import Header from './Header.vue'
    export default{
        name : "Add",
        
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