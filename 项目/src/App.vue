<script setup>
import { ref } from 'vue'
import axios from 'axios'

getlist()

const value = ref('')
const list = ref([])

async function getlist(){
 const res= await axios({
     
    url:"https://spv83z9g6h.bja.sealos.run/0clock-coding-isit-right",
   method:"GET",
  })
  list.value =res.data.list
  console.log(res);
}

async function add() {
 await axios({
  url:"https://spv83z9g6h.bja.sealos.run/fucking-add-plz",
  method:"POST",
  data:{
    value:value.value,
    isCompleted:false,
  },
 })
 getlist()
 value.value=''
}

async function update(id) {
await axios({
  url:"https://spv83z9g6h.bja.sealos.run/update-orz",
  method:"POST",
  data:{
   id,
  },
})
  getlist()
}

async function del(id) {
  await axios({
   url:"https://spv83z9g6h.bja.sealos.run/dellllll",
   method:"POST",
   data:{
    id: id,
   },
  })
  getlist()
}

</script>

<template>
  <div class="tou">
    <div class="ti">皇上这是你今天要翻的牌子</div>

    <div class="form">
      <input
        v-model="value"
        type="text"
        class="input"
        placeholder="选择你的英雄"
      />
      <div @click="add" class="button">加牌子</div>
    </div>

    <div
      v-for="(item, index) in list"
      :class="[item.isCompleted ? 'completed' : 'item']"
    >
      <div>
        <input @click="update(item._id)"  v-model="item.isCompleted" type="checkbox" />
        <span class="name">{{ item.value }}</span>
      </div>

      <div @click="del(item._id)" class="del">del</div>
    </div>
  </div>
</template>

<style scoped>
.tou {
  box-sizing: border-box;
  margin-top: 40px;
  margin-left: 1%;
  padding-top: 30px;
  width: 98%;
  height: 500px;
  background: #ffffff;
  border-radius: 5px;
  opacity: 0.8;
}

.ti {
  text-align: center;
  font-size: 30px;
  font-weight: 700;
}

.form {
  
  display: flex;
  justify-content: center;
  margin: 20px 0 30px 20px;
}

.button {
  width: 100px;
  height: 52px;
  border-radius: 0 20px 20px 0;

  text-align: center;
  background: linear-gradient(
    to right,
    rgb(113, 65, 168),
    rgba(44, 114, 251, 1)
  );
  color: #fff;
  line-height: 52px;
  cursor: pointer;
  font-size: 14px;
  user-select: none;
  
}

.input {
  padding: 0px 15px 0px 15px;
  border-radius: 20px 0 0 20px;
  border: 1px solid #dfe1e5;
  outline: none;
  width: 60%;
  height: 50px;
}

.item {
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 80%;
  height: 50px;
  margin: 8px auto;
  padding: 16px;
  border-radius: 20px;
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 20px;
}

.del {
  color: red;
}

.completed {
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 80%;
  height: 50px;
  margin: 8px auto;
  padding: 16px;
  border-radius: 20px;
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 20px;
  text-decoration: line-through;
  opacity: 0.4;
}
</style>
