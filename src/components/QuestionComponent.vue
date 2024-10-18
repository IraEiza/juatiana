<template>
  <div class="h-screen bg-cover bg-center flex justify-center items-center">
    <div class="w-[1200px] h-[350px] px-4 py-8 bg-red-500 bg-opacity-60 rounded-xl shadow-md text-white text-center">
      <div v-if="currentQuestion" class="h-full flex flex-col justify-between">
        <div class="text-4xl font-bold mb-6">{{ currentQuestion.question }}</div>
        <!-- Respuestas en formato 2x2 con estilo unificado -->
        <div class="grid grid-cols-2 gap-4">
          <button
            v-for="(answer, index) in currentQuestion.answers"
            :key="index"
            @click="selectAnswer(index)"
            class="p-4 bg-white text-pink-500 font-bold rounded-md shadow-lg hover:bg-pink-100 hover:text-yellow-500 hover:shadow-pink-400 transition-all duration-300 ease-in-out transform hover:scale-110 cursor-pointer"
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
  