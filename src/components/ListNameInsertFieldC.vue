<template>
 <div class="container">
<input type="text" v-model="NewlistName">
<button @click="ArrayCreator"> Create a new array </button>
 </div>
</template>

<script>
export default {
  name: 'ListNameInsertFieldC',
data(){
  return{
NewlistName : ""

  }
},
methods:{
  ArrayCreator(){
    this.$emit("NewArrCreator", this.NewlistName);
  }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
