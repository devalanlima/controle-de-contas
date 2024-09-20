<template>
      <label class="cursor-pointer">
        <div 
          class="w-3 h-3 transition-all ease-in-out duration-150 ring-2 border-2 border-white ring-transparent outline-2 outline outline-gray-800"
          :class="inputCheckbox ? 'bg-gray-800' : 'bg-white'"
        >
        </div>
      <input class="sr-only" type="checkbox" v-model="inputCheckbox" />
    </label>
</template>

<script setup lang="ts">
import { computed } from 'vue'

interface Props {
  modelValue: boolean
}

const props = defineProps<Props>()

const emit = defineEmits<{
  'update:modelValue': [value: typeof props.modelValue]
}>()

const inputCheckbox = computed({
  get() {
    return props.modelValue
  },
  set(inputCheckbox) {
    emit('update:modelValue', inputCheckbox)
  }
})

</script>