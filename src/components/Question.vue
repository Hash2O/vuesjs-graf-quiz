<template>
    <div class="question">
        <h3>{{ question.question }}</h3>
        <ul>
            <li v-for="(choice, index) in randomChoices" :key="choice">
                <label :for="`answer${index}`">
                    <input 
                        :id="`answer${index}`" 
                        type="radio" 
                        name="answer"
                        v-model="answer"
                        :value="choice">
                    {{ choice }}
                </label>
            </li>
        </ul>
        <button :disabled="!hasAnswered" @click="emits('answer', answer)">Question suivante</button>
    </div>
</template>

<script setup>
import { shuffleArray } from '@/functions/array';
import { ref, computed } from 'vue';

const props = defineProps({
    question: Object
})
const emits = defineEmits(['answer'])
const answer = ref(null)
const hasAnswered = computed(() => answer.value !== null)
const randomChoices = computed(() => shuffleArray(props.question.choices))
</script>

<style>
    .question {
        padding-top: 2rem;
    }
    .question button {
        margin-left: auto;
        display: block;
    }
</style>
