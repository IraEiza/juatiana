<template>
    <div class="p-4 bg-gray-100 rounded-md shadow-md">
      <div v-if="currentQuestion">
        <div class="text-xl font-bold mb-4">{{ currentQuestion.question }}</div>
        <div class="flex flex-col gap-4">
          <button
            v-for="(answer, index) in currentQuestion.answers"
            :key="index"
            @click="selectAnswer(index)"
            class="p-2 bg-blue-500 text-white rounded-md hover:bg-blue-600"
          >
            {{ answer }}
          </button>
        </div>
      </div>
      <div v-else>
        <div class="text-center text-2xl">¡Has completado todas las preguntas!</div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, watch } from 'vue'
  
  const props = defineProps({
    questions: Array,
    currentQuestionIndex: Number
  })
  
  const emit = defineEmits(['next-question'])
  
  const currentQuestion = ref(null)
  
  watch(
    () => props.currentQuestionIndex,
    () => {
      currentQuestion.value = props.questions[props.currentQuestionIndex]
    },
    { immediate: true }
  )
  
  const selectAnswer = (index) => {
    // Aquí puedes manejar la respuesta seleccionada
    console.log('Respuesta seleccionada:', currentQuestion.value.answers[index])
    emit('next-question')
  }
  </script>
  