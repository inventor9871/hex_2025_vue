<template>
  <h1>week1</h1>
  <table>
  <thead>
    <tr>
      <th scope="col">品項</th>
      <th scope="col">描述</th>
      <th scope="col">價格</th>
      <th scope="col">庫存</th>
    </tr>
  </thead>
  <tbody>
    
    <tr v-for="item in items" :key="item.id">
      <!-- <div class="bd1"> -->
      <td  class="bd1"><button type="button" @click="editItem(item)">編輯</button>
        {{ item.product }}</td>
      <td  class="bd1">{{ item.desc }}</td>
      <td  class="bd1">{{ item.price }}</td>
      <td  class="bd1"><button type="button" @click="item.stock--">-</button>
        {{ item.stock }}
        <button type="button" @click="item.stock++">+</button></td>
      <!-- </div> -->
    </tr>
  </tbody>
</table>
<br />
<div v-if="editItem_TF === true">
  品項：<input type="text" v-model="tempItem.product"><br />
  描述：<input type="text" v-model="tempItem.desc"><br />
  價格：<input type="number" v-model="tempItem.price"><br />
  <button type="button" @click="yesEdit">確認</button>
  <button type="button" @click="noEdit">取消</button><br />
</div>
</template>
<!-- ******* -->
<script setup>
import { ref } from 'vue';

const tempItem = ref({});
const editItem_TF = ref(false)
const items = ref([
    {id: 1,
      product: '珍珠奶茶' ,
      desc: '香濃奶茶搭配QQ珍珠' ,
      price: 50 ,
      stock:20  
    },
    {id: 2,
      product: '冬瓜檸檬' ,
      desc: '清新冬瓜配上新鮮檸檬' ,
      price: 45 ,
      stock: 18 
    },
    {id: 3,
      product: '翡翠檸檬' ,
      desc: '綠茶與檸檬的完美結合' ,
      price: 55 ,
      stock: 34 
    },
    {id: 4,
      product: '四季春茶' ,
      desc: '香醇四季春茶，回甘無比' ,
      price: 45 ,
      stock: 10 
    },
    {id: 5,
      product: '阿薩姆奶茶' ,
      desc: '阿薩姆紅茶搭配香醇鮮奶' ,
      price: 50 ,
      stock: 25 
    },
    {id: 6,
      product: '芒果綠茶' ,
      desc: '芒果與綠茶的獨特風味' ,
      price: 55 ,
      stock:  18
    },
    {id: 7,
      product: '檸檬冰茶' ,
      desc: '檸檬與冰茶的清新組合'  ,
      price: 45 ,
      stock:  20
    },
    {id: 8,
      product: '抹茶拿鐵' ,
      desc: '抹茶與鮮奶的絕配' ,
      price: 60 ,
      stock:  20
    },
  ]);

const editItem = (item)=>{
  tempItem.value = {...item};
  editItem_TF.value = true;
}

const yesEdit = ()=>{
  const index = items.value.findIndex(item=>item.id === tempItem.value.id);
  // console.log(index);
  items.value[index] = tempItem.value;
  // tempItem.value = {};
  editItem_TF.value = false;
}
const noEdit = ()=>{
tempItem.value = {};
editItem_TF.value = false;
}


</script>
<!-- ******* -->
<style>
.bd1{
  border-bottom: 1px solid #000;
}
</style>