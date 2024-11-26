<template>
  <div>
    {{ quiz }}
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';

const quiz = ref(null)

onMounted(() => {
  fetch('/quiz.json')
    .then(result => {
      if(result.ok) {
        return result.json()
      }
      throw new Error("Impossible de récupérer le fichier json")
    })
    .then(data => {
      quiz.value = data
    })
})
</script>