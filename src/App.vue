<template>
  <div class="p-10 h-screen bg-[url('./public/downwards_heart_bg.gif')] bg-cover bg-center flex justify-center items-center">
    <div v-if="show_title" class="flex flex-col gap-10 items-center bg-red-500 bg-opacity-80 p-20 rounded-xl">
        <div class="font-bold text-6xl text-center text-white">M.I.R.A.M.O</div>
        <div class="text-xl">Método por IA de Reboot Academy para la detección de Matrimonios Óptimos</div>
        <div class="h-64 w-64 bg-[url('./public/AI_love.webp')] bg-contain my-12"></div>
        <div class="text-lg p-4 bg-white font-bold rounded-md shadow-md shadow-lg hover:bg-pink-400 hover:text-yellow-200 hover:shadow-pink-400 transition-all duration-300 ease-in-out transform hover:scale-110 focus:outline-none cursor-pointer" @click="startQuestions">Click para comenzar</div>
    </div>
    <div v-else-if="current_question < questions.length">
      <QuestionComponent
        :questions="questions"
        :currentQuestionIndex="current_question"
        @next-question="nextQuestion"
      />
    </div>
    <div v-else>
      <transition name="fade">
        <FinalScreen v-if="current_question >= questions.length" @restart="restartQuiz" />
      </transition>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import QuestionComponent from './components/QuestionComponent.vue'
import FinalScreen from './components/FinalScreen.vue'

const questions = ref([
  {
    "question": "¿Qué harías si tu pareja deja siempre la tapa del inodoro levantada?",
    "answers": [
      "La bajo en silencio, pero lo recuerdo en cada discusión.",
      "Le dejo una nota pegajosa en el baño para que lo aprenda.",
      "¡No me importa, lo bajo yo mismo/a!",
      "Empezamos la guerra del baño… ¡quien olvide la tapa, paga!"
    ]
  },
  {
    "question": "Si tu pareja se olvida constantemente de las fechas importantes, como aniversarios o cumpleaños, ¿qué harías?",
    "answers": [
      "Le lo recordaría con sutileza días antes.",
      "Lo dejo pasar, pero me acuerdo la próxima vez que olvide algo.",
      "Organizo una celebración sorpresa… solo para mí.",
      "Hago que se sienta culpable hasta que lo anote en su calendario."
    ]
  },
  {
    "question": "¿Qué haces cuando tu pareja siempre se adueña del control remoto de la TV?",
    "answers": [
      "Le dejo elegir, pero me aseguro de que sea algo que me guste.",
      "Le cambio el canal cuando se va al baño, ¡y que no se dé cuenta!",
      "Me resigno y uso el móvil mientras tanto.",
      "¡Empiezo una batalla por el control cada noche!"
    ]
  },
  {
    "question": "Si tu pareja nunca responde a tus mensajes a tiempo, ¿cómo reaccionas?",
    "answers": [
      "Le mando más mensajes hasta que conteste.",
      "Lo llamo para preguntarle si ha visto el teléfono.",
      "Me hago el/la ofendido/a, pero me dura 5 minutos.",
      "Lo ignoro, ¡seguro está ocupado/a!"
    ]
  },
  {
    "question": "¿Qué harías si tu pareja siempre deja los platos sucios en el fregadero?",
    "answers": [
      "Los lavo, pero lo anoto mentalmente.",
      "Le digo que lo haga de inmediato, ¡sin excusas!",
      "Dejo los míos también para que note la indirecta.",
      "Ignoro el problema hasta que sea él/ella quien los lave."
    ]
  },
  {
    "question": "Tu pareja tiende a gastar mucho en compras innecesarias. ¿Cómo lo manejas?",
    "answers": [
      "Lo hablo y establecemos un presupuesto juntos.",
      "Lo dejo, mientras lo que compre también me sirva.",
      "Empiezo a esconder la tarjeta de crédito por 'precaución'.",
      "¡Cada uno con su dinero, y nadie se mete en lo del otro!"
    ]
  },
  {
    "question": "¿Qué harías si tu pareja siempre tarda una eternidad en arreglarse antes de salir?",
    "answers": [
      "Le aviso con una hora extra de anticipación.",
      "Me pongo a hacer algo mientras espero… y espero… y espero.",
      "Me resigno, pero lo menciono cada vez que llegamos tarde.",
      "Me cambio de ropa dos veces para matizar la espera."
    ]
  },
  {
    "question": "Tu pareja tiene la manía de quedarse pegada al móvil durante las comidas. ¿Qué harías?",
    "answers": [
      "Le pido que lo guarde para que podamos hablar.",
      "Tomo mi móvil también, ¡dos pueden jugar ese juego!",
      "Le hago preguntas hasta que lo deja de lado.",
      "Le desconecto el WiFi y lo miro con cara inocente."
    ]
  },
  {
    "question": "¿Qué haces cuando tu pareja nunca se ofrece a ayudar con la limpieza?",
    "answers": [
      "Le asigno tareas específicas para que no haya excusas.",
      "Le dejo una lista escrita de lo que tiene que hacer.",
      "Ignoro el problema hasta que se dé cuenta (ojalá…).",
      "Hago la limpieza yo solo/a mientras pongo mi música favorita."
    ]
  },
  {
    "question": "Si tu pareja nunca se acuerda de dónde pone las cosas, ¿cómo reaccionas?",
    "answers": [
      "Lo ayudo a buscar mientras me río de la situación.",
      "Me adelanto y guardo yo las cosas importantes.",
      "Lo dejo buscar solo/a hasta que lo encuentre.",
      "Le doy pistas como si fuera un juego de 'caliente/frío'."
    ]
  }
]
)

const current_question = ref(0)
const show_title = ref(true)

const startQuestions = () => {
  show_title.value = false
}

const nextQuestion = () => {
  if (current_question.value < questions.value.length - 1) {
    current_question.value++
  } else {
    // Cuando llegamos a la última pregunta, mantenemos el contador en el mismo lugar.
    current_question.value = questions.value.length
  }
}

const restartQuiz = () => {
  current_question.value = 0
  show_title.value = true
}
</script>
