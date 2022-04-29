<script setup>
import { ref } from "@vue/reactivity"

defineProps([])
const emit = defineEmits(['selectPrd'])
const prds = {
  'gold': {
    name: '黃金',
    id: '573004'
  },
  'silver': {
    name: '白銀',
    id: '573005'
  },
  'oil': {
    name: '原油',
    id: '573006'
  }
}
const selectedPrds = ref([])
const selectPrd = (prd)=>{
  console.log(prd);
  emit('selectPrd', selectedPrds.value)
}
</script>

<template>
  <div class="greetings">
    <div v-for="prd in prds" :key="prd.name">
      <input type="checkbox" :name="prd.name" :id="prd.name" :value="prd" v-model="selectedPrds"
        @change="selectPrd(prd)">
      <label :for="prd.name">
        <span> {{ prd.name }} </span>
      </label>
    </div>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {

  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
