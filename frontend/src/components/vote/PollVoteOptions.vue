<template>
  <div class="space-y-3">
    <div 
      v-for="(option, index) in options" 
      :key="index"
      @click="$emit('update:modelValue', index)"
      class="p-5 rounded-2xl border-2 transition-all duration-200 cursor-pointer flex items-center justify-between group"
      :class="modelValue === index ? 'border-amber-400 bg-amber-50/50 shadow-md' : 'border-gray-200 hover:border-gray-300 bg-gray-50/50'"
    >
      <div class="flex items-center space-x-4">
        <!-- Radio Circle -->
        <div 
          class="w-6 h-6 rounded-full border-2 flex items-center justify-center transition-all flex-shrink-0"
          :class="modelValue === index ? 'border-amber-500 bg-amber-400' : 'border-gray-300 bg-white group-hover:border-gray-400'"
        >
          <div v-if="modelValue === index" class="w-2.5 h-2.5 rounded-full bg-black"></div>
        </div>

        <!-- Poll Option Text -->
        <span 
          class="text-base sm:text-lg font-bold transition-colors"
          :class="modelValue === index ? 'text-black' : 'text-gray-700'"
        >
          {{ option.text }}
        </span>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  options: {
    type: Array,
    required: true
  },
  modelValue: {
    type: Number,
    default: null
  }
})

// Define the emit event for two-way binding -->
defineEmits(['update:modelValue'])
</script>
