<template>
  <div class="final-screen-container p-10 h-45 bg-red-500 bg-opacity-80 flex flex-col items-center justify-center">
    <div class="text-white text-5xl font-bold mb-6">¡Felicidades!</div>
    <div class="text-white text-2xl mb-4 text-center">Has completado el cuestionario de M.I.R.A.M.O</div>
    <div class="text-white text-xl text-center">Tu compatibilidad ha sido evaluada exitosamente.</div>
    <div class="mt-10">
      <!-- Botón estilizado con tema romántico -->
      <button @click="restartQuiz" class="px-6 py-3 bg-white text-pink-500 font-bold rounded-full shadow-lg hover:bg-pink-100 hover:text-yellow-500 hover:shadow-pink-400 transition-all duration-300 ease-in-out transform hover:scale-110 cursor-pointer">
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
