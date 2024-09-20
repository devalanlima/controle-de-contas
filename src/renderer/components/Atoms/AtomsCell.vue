<template>
  <div 
  class="px-2 h-[50px] outline outline-1 flex items-center justify-center"
  :class="severity[props.severity]"
  >
    <slot/>
  </div>
</template>

<script setup lang="ts">
import { Severity } from '../../typings/severity'

interface Props {
  severity?: Severity
}

const props = withDefaults(defineProps<Props>(), {
  severity: 'neutral'
})

const severity = {
  'dark': 'bg-gray-800 text-gray-200 outline-gray-200',
  'light': 'bg-gray-200 text-gray-800 outline-gray-800',
  'neutral': 'bg-gray-600 text-gray-200 outline-gray-800',
  'paid': 'bg-green-200 text-gray-800 outline-gray-800',
  'pending': 'bg-yellow-200 text-gray-800 outline-gray-800',
  'overdue': 'bg-red-300 text-gray-800 outline-gray-800',
}

</script>