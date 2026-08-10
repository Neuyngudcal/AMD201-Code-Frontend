<template>
  <button 
    :type="type" 
    :disabled="disabled"
    @click="$emit('click', $event)"
    :class="[
      'w-full sm:w-auto px-8 py-4 font-extrabold text-base rounded-full transition-all duration-200 shadow-xl flex items-center justify-center space-x-2',
      disabled ? 'opacity-50 pointer-events-none' : 'hover:scale-105',
      variant === 'primary' 
        ? 'bg-gradient-to-r from-amber-400 to-amber-500 hover:from-amber-300 hover:to-amber-400 text-black hover:shadow-amber-400/20' 
        : 'bg-white text-black border border-gray-200 hover:bg-gray-50'
    ]"
  >
    <slot></slot>
  </button>
</template>

<script setup>
defineProps({
  type: {
    type: String,
    default: 'button'
  },
  disabled: {
    type: Boolean,
    default: false
  },
  variant: {
    type: String,
    default: 'primary'
  }
});
defineEmits(['click']);
</script>
