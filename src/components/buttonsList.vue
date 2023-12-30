<script setup lang="ts">
import {ref} from 'vue';
const props = defineProps<{
  begin: number
  end: number
  current: number
}>();
const current = ref(props.current);
const arr = [...Array(props.end-props.begin+1)].map((_, i) => i+props.begin) //=> [ 0, 1, 2, 3, 4 ]
</script>

<template>
  <div>
  <div class="ct" v-for="item in arr" :key="item">
    <button class="btn highlight" @click="current=item;$emit('update',current)" v-if="item==props.current">{{ item }}</button>
    <button class="btn" @click="current=item;$emit('update',current)" v-else>{{ item }}</button>
  </div>
  <input class="ipt" v-model="current" @input="$emit('update',current)">
</div>
</template>

<style scoped>
.ct{
  float: left;
}
.highlight{
  background-color: #fcc;
}
.btn{
  width: 50px;
  height: 30px;
  border: 1px solid #000;
  border-radius: 5px;
  margin: 2px;
}
.ipt{
  width: 60px;
  height: 27px;
  border: 1px solid #000;
  border-radius: 5px;
  margin: 2px;
}
</style>
