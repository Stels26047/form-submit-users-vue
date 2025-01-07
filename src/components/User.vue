<script>

    export default{
        props: {
            user:{
                type: Object,
                required: true
            },
            index:{
                type: Number,
                required: true
            },
            deleteUser:{
                type: Function,
                required: true
            }
        }
    }

</script>

<template>

    <div className="user">
        <button @click="deleteUser(index)">Удалить</button>
        <p>{{ user.name }}</p>
        <p>{{ user.pass }} - <b>{{ user.email }}</b></p>
    </div>

</template>

<style scoped>

    button{
        border:0;
        border-radius: 5px;
        outline:none;
        padding:  10px 15px;
        background:  #d66c75;
        color:#7f1629;
        font-weight:bold;
        cursor: pointer;
        transition: transform 500ms ease;
        float: right;
    }

</style>