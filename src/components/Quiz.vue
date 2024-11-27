<template>
    <h1>{{ quiz.title }}</h1>
    <ProgressBar :value="step" :max="quiz.questions.length - 1" />
    <Question :question="question" v-if="question"/>
</template>

<script setup>
import { computed, ref } from 'vue';
import ProgressBar from './ProgressBar.vue';
import Question from './Question.vue';

    const props = defineProps({
        quiz: Object
    })

    const step = ref(0)
    const question = computed(() => props.quiz.questions[step.value])
</script>
