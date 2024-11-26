<template>
    <h1>{{ quiz.title }}</h1>
    <ProgressBar :value="step" :max="quiz.questions.length - 1" />
</template>

<script setup>
import { ref } from 'vue';
import ProgressBar from './ProgressBar.vue';

    defineProps({
        quiz: Object
    })

    const step = ref(0)
</script>
