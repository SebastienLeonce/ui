<template>
  <div class="n-text-input n-bg-base focus-within:n-focus-base focus-within:border-context rounded px-2 py-1 border n-border-base flex items-center flex">
    <slot name="icon">
      <NIcon v-if="icon" :icon="icon" class="mr-0.4em text-1.1em op50" />
    </slot>
    <textarea 
      v-model="input"
      class="!outline-none flex-auto n-bg-base"
      :rows="rows"
      :minlength="minlength"
      :maxlength="maxlength"
      :placeholder="placeholder"
      :disabled="disabled"
    />
  </div>
</template>

<script setup lang="ts">
import { useVModel } from '@vueuse/core'

const props = withDefaults(
  defineProps<{
    modelValue?: string
    placeholder?: string
    icon?: string
    disabled?: boolean
    rows?: number
    minlength?: number
    maxlength?: number
  }>(),
  {
    modelValue: '',
    disabled: false
  }
)
const emit = defineEmits<{(...args: any): void}>()
const input = useVModel(props, 'modelValue', emit, { passive: true })
</script>
