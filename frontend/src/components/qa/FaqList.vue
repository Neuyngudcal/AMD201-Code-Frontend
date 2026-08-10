<template>
  <div class="space-y-4">
    <div 
      v-for="(faq, faqIndex) in faqs" 
      :key="faqIndex"
      class="bg-white rounded-2xl border shadow-sm overflow-hidden transition-all duration-300 hover:border-black"
      :class="[
        activeIndex === faqIndex ? 'border-amber-400 ring-1 ring-amber-400 bg-amber-50/20' : 'border-gray-200/80'
      ]"
    >
      <button 
        @click="toggleFaq(faqIndex)"
        class="w-full text-left px-6 py-5 flex justify-between items-center focus:outline-none"
      >
        <span class="font-bold text-base sm:text-lg text-black">{{ faq.question }}</span>
        
        <!-- Icon mũi tên, xoay 180 độ nếu đang mở -->
        <span class="ml-4 flex-shrink-0 flex items-center justify-center w-8 h-8 rounded-full border border-gray-300 text-black transition-all duration-300"
              :class="{'bg-black text-white border-black rotate-180': activeIndex === faqIndex}">
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path>
          </svg>
        </span>
      </button>
      <div 
        v-show="activeIndex === faqIndex"
        class="px-6 pb-6 text-gray-600 text-sm sm:text-base leading-relaxed border-t border-gray-100 pt-4"
      >
        {{ faq.answer }}
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const activeIndex = ref(0)
const faqs = [
  {
    question: "Do I need to create an account or log in to create a poll?",
    answer: "No! Pollco is built for zero friction. You can create, share, and vote on polls instantly without registering, entering a password, or verifying your email."
  },
  {
    question: "How do I control and edit a poll without a user account?",
    answer: "When you publish a poll, our system securely generates an Admin Token and saves it in your device's browser local storage. Using this token, our system recognizes you as the creator, allowing you to edit questions, add options, close voting, or delete the poll anytime."
  },
  {
    question: "Can I share my poll across messaging apps and social media?",
    answer: "Yes, every poll generates a clean universal short link (e.g., /poll/pPNXiZQ). Anyone with the link can vote with a single click from any smartphone, tablet, or desktop computer."
  },
  {
    question: "How fast do poll results and percentage charts update?",
    answer: "Our analytics dashboard features real-time live polling. Results and leading option percentages automatically refresh every 5 seconds so your community can watch the consensus unfold live."
  }
]

const toggleFaq = (faqIndex) => {
  activeIndex.value = activeIndex.value === faqIndex ? null : faqIndex
}
</script>
