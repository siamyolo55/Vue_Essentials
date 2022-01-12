<template>
    <h1> Home Page </h1>
</template>

<script>
    export default{
        name : "Home",

        mounted(){
            let info = localStorage.getItem('user-info')
            if(!info){
                this.$router.push({name : "SignUp"})
            }
        }
    }
</script>