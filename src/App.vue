<template>
  <div id="app">
    <img src="./assets/logo.png" >
    <!-- <router-view></router-view> -->
    <this-input :msg="parentMsg" v-on:message="receiveMsg"></this-input>  
    <this-dialog></this-dialog>
    <carousel></carousel>  
  </div>
</template>

<script>
import thisInput from './components/input'
import thisDialog from './components/dialog'
import carousel from './components/carousel'
import Vue from 'vue'
export default {
  components: {
    thisInput,
    thisDialog,
    carousel
  },
  data(){
    return {
        parentMsg:[
          {
            name:'Jepson',
            age:26
          },
          {
            name:'Mike',
            age:24
          },
          {
            name:'Alice',
            age:19
          }
        ],
        flag:false,
        Hub:new Vue({})
    }
  },
  methods:{
    receiveMsg(val){
      this.flag=val;
    },
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
