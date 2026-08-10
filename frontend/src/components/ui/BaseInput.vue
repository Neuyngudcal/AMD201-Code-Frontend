<template>
  <div class="space-y-3">
    <!-- Hiển thị Label nếu có truyền vào -->
    <label v-if="label" class="block text-sm font-bold text-gray-700">
      {{ label }} <span v-if="required" class="text-red-500">*</span>
    </label>
    
    <div class="relative">
      <input 
        :type="type"
        :placeholder="placeholder"
        :value="modelValue"
        @input="(e) => { $emit('update:modelValue', e.target.value); $emit('input', e) }"
        class="w-full px-5 py-4 bg-gray-50/80 border-2 border-gray-200 rounded-2xl text-base sm:text-lg font-semibold text-black placeholder-gray-400 focus:bg-white focus:border-black focus:outline-none transition-all duration-200 shadow-sm"
      />
    </div>
  </div>
</template>

<script setup>
defineProps({
  label: {
    type: String,
    default: ''
  },
  required: {
    type: Boolean,
    default: false
  },
  type: {
    type: String,
    default: 'text'
  },
  placeholder: {
    type: String,
    default: ''
  },
  modelValue: {
    type: [String, Number],
    default: ''
  }
});

defineEmits(['update:modelValue', 'input']);
</script>
