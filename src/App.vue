<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import { ElTag, ElButton } from 'element-plus'
import { ref, reactive } from 'vue'

  const haha=ref('姓名');
  const hehe=ref('電話');

  
  let id=1;
  const obj=ref([{id:id++,name:'eason',phone:123,dis:true}, 
             {id:id++,name:'yoro',phone:123343,dis:true},
             {id:id++,name:'nana',phone:45678,dis:true}])
  
  const insert=()=> {
      obj.value.push({id:id++,name:haha.value,phone:hehe.value,dis:true})
       haha.value='';
       hehe.value='';
  }
  const deleteBtn=(v)=>{
     v.dis=false
  }
  
</script>

<template>

  <input v-model="haha"> <input v-model="hehe"><button @click="insert">新插入一筆</button>
  <ul v-for="v in obj"  v-show="v.dis">
    <li>{{v.id}},{{v.name}},{{v.phone}}<button @click='deleteBtn(v)'>x</button></li>
  </ul>

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
