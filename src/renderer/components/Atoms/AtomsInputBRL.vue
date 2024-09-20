<template>
  <input 
    class="bg-transparent focus:outline-none focus:border-none w-[90px] font-semibold"
    type="text" 
    :value="inputValue"
    @input="handleInput"
  />
</template>

<script setup lang="ts">
import { ref } from 'vue'

interface Props {
  modelValue: string | number 
}

type Emit = {
  'update:modelValue': [value: typeof props.modelValue]
}

const props = defineProps<Props>()

const emit = defineEmits<Emit>()

const inputValue = ref(props.modelValue)

const handleInput = (event: Event) => {
  const $input = event?.target as HTMLInputElement
  inputValue.value = parseFloat($input.value.replace(/[^\d]/g, '')) / 100    
  inputValue.value = isNaN(inputValue.value) ? 'R$ 0,00' : formatToBRL(inputValue.value)
  emit('update:modelValue', inputValue.value)
}

function formatToBRL(amount: number) {  
    return new Intl.NumberFormat('pt-BR', {
      style: 'currency',
      currency: 'BRL',
    }).format(amount)
}

</script>