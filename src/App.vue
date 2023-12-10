<template>
  <HelloWorld firstName="Ivan" lastName="Ivanov" v-bind:email="email" avatar="70.jpg" />
    <HelloWorld firstName="Ivan" lastName="Ivanov" v-bind:email="email" avatar="70.jpg" />

  <HelloWorld firstName="Ivan" lastName="Ivanov" v-bind:email="email" avatar="70.jpg" />

  <HelloWorld firstName="Ivan" lastName="Ivanov" v-bind:email="email" avatar="70.jpg" />

  <button @click="getUserData">BUTTON</button>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data()
  {
    return {
    email: '',
    firstName: '',
    lastName: ''
    }
  },
  methods:
  {
    getUserData()
    {
      this.axios.get('https://randomuser.me/api/').then( (response) =>{
        console.log(response.data.email)
        this.email = response.data.results[0].email // подставляем данные из ответа от сервера
      })
    }
  },
  mounted(){
    this.getUserData();
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
