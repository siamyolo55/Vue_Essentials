<template>
    <img class="logo" src="../assets/res_logo.png">
    <h1> SignUp </h1>
    <div class="register">
        <input type="text" placeholder="Enter name"/>
        <input type="text" placeholder="Enter email"/>
        <input type="password" placeholder="Enter password"/>
        <button>Sign Up</button>
    </div>
</template>

<script>
    export default{
        name : 'SignUp'
    }
</script>

<style>
    .logo{
        width: 300px
    }
    .register input{
        width: 300px;
        height: 40px;
        padding-left: 20px;
        display: block;
        margin-bottom: 30px;
        margin-left: auto;
        margin-right: auto;
        border: 1px solid skyblue;
    }

    .register button{
        width: 320px;
        height: 40px;
        border: 1px solid skyblue;
        background: skyblue;
        color: #fff;
        cursor: pointer;
        }
</style>