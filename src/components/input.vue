<template>
  <div class="hello">
    <!-- <h1>{{ msg }}</h1> -->
    <template>
      <input type="text" v-model="tips" name=""  @change="onInput()">
       <ul>
          <li v-for="(item,index) in msg">
             <p>{{item.name}}</p>
             <p>{{item.age}}</p>
          </li>
       </ul>
    </template>
  </div>
</template>

<script>
export default {
  props:{
    msg:Array
  },
  data(){
    return {
      flag:true,
      tips:'请输入值'
    }
  },
  methods:{
    onInput(){
      if(this.tips.trim()){
          this.$root.$emit('change',this.flag);
      } 
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
