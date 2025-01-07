<script>

  import User from './components/User.vue'

  export default{
    components: {User},
    data(){
      return{
        users:[],
        error: '',
        userName: '',
        userPass: '',
        userEmail: ''
      }
    },
    methods:{
      sendData(){

        if(this.userName == ''){ 
          this.error = 'Имя не введено';
          return
        } else if(this.userPass == ''){
          this.error = 'Пароль не введен';
          return
        } else if( this.userEmail == ''){
          this.error = 'Email не введен';
          return
        }

        this.error = '';

        this.users.push(
          {
            name: this.userName,
            pass: this.userPass,
            email: this.userEmail
          }
        );
      },

      deleteUser(index){
        this.users.splice(index,1);
      }
    }
  }

</script>

<template>

  <input type="text" v-model="userName" placeholder="Имя">
  <input type="password" v-model="userPass" placeholder="Пароль">
  <input type="email" v-model="userEmail" placeholder="email">
  <p className="error">{{ error }}</p>
  <button @click="sendData()">Отправить</button>
  <div className="user">
    <snap v-if="users.length == 0"> У нас нет пользователей</snap>
    <snap v-else-if="users.length == 1">У вас {{ this.users.length }} пользователь</snap>
    <snap v-else-if="users.length > 1 && users.length < 5">У вас {{ this.users.length }} пользователя</snap>
    <snap v-else>У вас {{ this.users.length }} пользователей</snap>
  </div>
  <User v-for="(el, index) in users" :key="index" :user="el" :deleteUser="deleteUser" />
</template>

<style scoped>
  input{
    display: block;
    margin-bottom: 10px;
    border-radius:  3px;
    border: 1px solid silver;
    outline:none;
    padding: 10px 15px;
    background: #fafafa;
    color:#333;
  }

  button{
    border:0;
    background: #6cd670;
    color:#167f3d;
    font-weight: bold;
    padding: 10px 15px;
    border-radius: 5px;
    outline: none;
    transition: transform 500ms ease;
    cursor: pointer;
  }

  button:hover{
    transform:  translateY(-5px);
  }

  .error{
    color:red;
  }

  .user{
    width: 500px;
    margin-top: 20px;
    border: 1px solid silver;
    background: #e3e3e3;
    color: #222;
    padding: 20px;
    border-radius: 5px;
  }
</style>
