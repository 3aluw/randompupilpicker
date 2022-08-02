<template>
  <ListNameInsertFieldC @NewArrCreator="newarrcreator"/>
  <div class="lists-container">
<div class="saved-list" v-for="(list, index) in lists" :key="list.number" @click="listExtrcat(index)"> 
 {{list.number}}
</div></div>
<button @click="selector">Pick someone</button>
<button @click="saver">Save List</button>
<h1>{{pickedP}}</h1>
</template>

<script>
import ListNameInsertFieldC from './components/ListNameInsertFieldC.vue'

export default {
  name: 'App',
  components: {
    ListNameInsertFieldC
  },

  data(){
    return{
      currentlist: null,
      listName: null,
    lists:[{
      number:1,
      arr: [0,1,2,3,4,5,6]
    },
    {
      number:2,
      arr: [0,1,2,3,4,5,6]
    },
    
    ],
      arr:[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30],
      workingArr :[],
      names:["تجرونة بشرى ","باباوموسى هدى","التومي مارية","بوحديبه غنية","موسى وعلي باية","بابنات مروة","شقبقب فاطمة الزهراء","أويابة سارة","قزريط أسماء","بوسنان سعاد","بوكرموش حفصة","الشيخ صالح فطيمة بنت","حمدي بابا مريم","بوكرموش سيرين","حجاج إسراء","امسيرد ضحى","ليسير بشرى","البدري رحمة","ارفيس فردوس","الشيخ صالح مارية","عوف نسيمة بنت","بازين سلسبيل","بوحديبه خديجة","اويابه بشرى","بابنات صفاء","عطفاوي مامه بنت","باباواسماعيل ملاك","طباخ زينب","قزريط إكرام","موسى وعلي زينب","أوزايد مامة لالة"]
     ,
     pickedP: null,
    }
  },
  methods:{
    listExtrcat(index){
this.workingArr = this.lists[index].arr;
/*this.currentlist = index;
this.listName = this.lists[index].number;
console.log(this.workingArr,this.lists[this.currentlist])
*/},
 selector(){
  
    if( this.workingArr.length === 0){
      this.workingArr = this.arr;  
    }
  let pickedN = Math.floor(Math.random()*this.workingArr.length);
  this.pickedP = this.names[this.workingArr[pickedN]]
  this.workingArr.splice(pickedN,1);
console.log(this.lists[this.currentlist].arr);

},
saver(){
  this.lists.splice(this.currentlist,1,{
    number: this.listName,
    arr: this.arr})  ;
  console.log(this.lists);
},
newarrcreator(name){
  this.lists.push({
    number : name,
    arr: this.arr
  });

  this.workingArr = this.lists[this.lists.length-1].arr;
this.currentlist = this.lists.length-1;
 this.listName = this.lists[this.lists.length-1].number;
   console.log(this.listName, this.lists)
}
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
.lists-container{
  display: flex;
  flex-direction: row;
}
.saved-list{
  margin: 0.5rem;
 min-height: 8rem;
 min-width:10rem ;
  border: 1px solid black;
  padding: 10px;
    display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;  
}
</style>
