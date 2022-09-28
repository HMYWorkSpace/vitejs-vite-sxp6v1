<script setup>
import { useAttrs, onUpdated } from 'vue';
const props = defineProps({
  title: {
    type: String,
    default: '测试1号',
  },
  modelValue: {
    type: String,
    default: '',
  },
});
const emits = defineEmits(['setTitle', 'update:modelValue', 'setText']);

function handleClick() {
  console.log('props', props);
}

function setVModel() {
  emits('update:modelValue', Math.random());
}

const attrs = useAttrs();
console.log('attrs', attrs);
onUpdated(() => {
  console.log('组件更新');
  console.log(attrs.text);
});
</script>
<template>
  <div @click="$emit('setTitle')">{{ title }}</div>
  <div @click="handleClick">子组件事件</div>
  <div>{{ modelValue }}</div>
  <div @click="setVModel">自定义v-model</div>
  <div>{{ $attrs.text }}</div>
  <div @click="$emit('setText')">设置文本</div>
</template>
<style></style>
