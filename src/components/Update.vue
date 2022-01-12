<template>
    <Header/>
    <h1> Update restaurant page</h1>
</template>


<script>
    import Header from './Header.vue'
    export default{
        name : "Update",
        
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