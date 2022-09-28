<script setup>
import { reactive, ref } from 'vue';
import Common1 from './Common1.vue';
const obj = reactive({
  arr: [
    {
      id: '1',
      name: '傻子1号',
    },
  ],
});
function add() {
  obj.arr.push({
    id: Math.random(),
    name: `傻子${Math.random()}号`,
  });
}

const newObj = {
  name: ref('Forjune'),
  age: ref(30),
};
const { name, age } = newObj;
function test(event, msg) {
  console.log('event', event);
  console.log('msg', msg);
  newObj.name.value = '傻子2号';
}

const title = ref('组件1');

function setTitle() {
  title.value = `组件${Math.random()}`;
}

const modelValue = ref('');
</script>

<template>
  <div v-for="item in obj.arr" :key="item.id">{{ item.name }}</div>
  <div>{{ name }}11</div>
  <div>{{ age }}12</div>
  <button @click="add">添加</button>
  <button @click="test($event, '测试参数')">测试</button>
  <div v-for="(value, key, index) in newObj" :key="key">{{ value }}</div>
  <Common1 @setTitle="setTitle" v-model="modelValue" v-bind="$attrs" />
</template>

<style scoped></style>
