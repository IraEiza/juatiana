<template>
    <div class="final-screen-container p-10 h-100 bg-green-500 flex flex-col items-center justify-center">
      <div class="text-white text-5xl font-bold mb-6">¡Felicidades!</div>
      <div class="text-white text-2xl mb-4 text-center">Has completado el cuestionario de M.I.R.A.M.O</div>
      <div class="text-white text-xl text-center">Tu compatibilidad ha sido evaluada exitosamente.</div>
      <div class="mt-10">
        <button @click="restartQuiz" class="px-6 py-3 bg-white text-green-500 font-bold rounded-md shadow-lg hover:bg-green-100 transition">
          Reiniciar cuestionario
        </button>
      </div>
    </div>
  </template>
  
  <script setup>
  const emit = defineEmits(['restart'])
  
  const restartQuiz = () => {
    emit('restart')
  }
  </script>
  
  