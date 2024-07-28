<template>
  <div class="main">
    <h1>testPage</h1>
    <p>count{{ count }}</p>
    <p>doubleCount{{ doubleCount }}</p>
    <button class="bt" type="button" @click="increment">add</button>
    <p ref="hello">count{{ count }}</p>
  </div>
</template>
<script setup>
import { useCounterStore } from '@/stores/counter'
import { storeToRefs } from 'pinia'
import { getCurrentInstance, ref, onMounted } from 'vue'

const { proxy } = getCurrentInstance()
const store = useCounterStore()
const { count, doubleCount } = storeToRefs(store)
const { increment } = store
onMounted(() => {
  console.log(proxy.$refs.hello)
})
</script>
<style scoped lang="less">
.main {
  width: 200px;
  .bt {
    font-size: 30px;
  }
}
</style>
