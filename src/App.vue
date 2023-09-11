<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import { ElTag, ElButton } from 'element-plus'
import { ref, reactive, computed } from 'vue'

  const haha=ref('姓名');
  const hehe=ref('代辦事項');
  const showControll=ref(false)
  let id=1;
  const obj=ref([{id:id++,name:'eason',phone:123,dis:true,checked:false}, 
             {id:id++,name:'yoro',phone:123343,dis:true,checked:false},
             {id:id++,name:'nana',phone:45678,dis:true,checked:false}])
  
  const insert=()=> {
    obj.value.push({id:id++,name:haha.value,phone:hehe.value,dis:true,checked:false})
       haha.value='';
       hehe.value='';
  }
  const deleteBtn=(v)=>{
     v.dis=false
  }
  const toggleCheckbox=(a)=>{
      a.checked = !a.checked; 
    }

  const showModel=computed(() => {
  return  showControll.value
    ? obj.value.filter((t) => !t.checked)
    : obj.value
})
</script>

<template>

  <input type ="text" v-model="haha"> <input type ="text" v-model="hehe">
  <p><button @click="insert">新插入一筆</button></p>
  <ul>
    <li v-for="va in showModel"  v-show="va.dis">
      <input type="checkbox" :checked='va.checked' 
      @change='toggleCheckbox(va)' >
      <span :class="va.checked?'letaa':''">{{va.id}},{{va.name}},{{va.phone}}</span>
      <button @click='deleteBtn(va)'>x</button>
    </li>
  </ul>
  <button @click="showControll=!showControll">{{showControll?'顯示全部':'只顯示未完成'}}</button>



</template>

<style scoped>
header {
  line-height: 1.5;
  
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

.try{
    display:none
  }

.letaa{
  color:red;
  text-decoration:line-through 
  
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }


}
</style>
