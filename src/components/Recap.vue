<template>
    <h1>Recap</h1>
    <p>
        Score : {{ score }} / {{ quiz.questions.length }}
    </p>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
    quiz: Object,
    answers: Array
})

const score = computed(() => {
    return props.quiz.questions.reduce((acc, question, index) => {
        if(question.correct_answer === props.answers[index]) {
            return acc+1
        }
        return acc
    }, 0)
})
</script>