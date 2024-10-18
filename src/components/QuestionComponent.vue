<template>
  <div class="p-10 h-screen bg-cover bg-center flex justify-center items-center">
    <div class="p-4 bg-red-500 bg-opacity-60 rounded-xl shadow-md text-white text-center">
      <div v-if="currentQuestion">
        <div class="text-4xl font-bold mb-6">{{ currentQuestion.question }}</div>

        <!-- Respuestas en formato 2x2 con estilo unificado -->
        <div class="grid grid-cols-2 gap-4">
          <button
            v-for="(answer, index) in currentQuestion.answers"
            :key="index"
            @click="selectAnswer(index)"
            class="p-4 bg-pink-500 text-white font-bold rounded-md shadow-lg hover:bg-pink-400 hover:text-yellow-200 transition-all duration-300 ease-in-out transform hover:scale-110 focus:outline-none cursor-pointer"
          >
            {{ answer }}
          </button>
        </div>
      </div>
      <div v-else>
        <div class="text-3xl font-bold">¡Has completado todas las preguntas!</div>
      </div>
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
  