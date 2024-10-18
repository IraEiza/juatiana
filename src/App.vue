<template>
  <div class="p-10 h-screen bg-red-400">
    <div v-if="show_title" class="flex flex-col gap-4 items-center">
      <div class="font-bold text-4xl text-center text-white">M.I.R.A.M.O</div>
      <div>Método por IA de Reboot Acadenmy para la detección de Matrimonios Óptimos</div>
      <div class="p-4 bg-white rounded-md shadow-md" @click="startQuestions">Click para comenzar</div>
    </div>
    <div v-else>
      Show question component
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const questions = ref([])
const current_question = ref(0)
const show_title = ref(true)

const startQuestions = () => {
  show_title.value = false
}
</script>
