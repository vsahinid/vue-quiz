<template>
    <div class="question-box-container">
        <b-jumbotron>
            <template #lead>
            {{ currentQuestion.question }}
            </template>

            <hr class="my-4">

            <b-list-group>
                <b-list-group-item v-for="(answer, index) in shuffledAnswers" :key="index" @click.prevent="selectAnswer(index)"
                :class="answerClass(index)">
                {{ answer }}
                </b-list-group-item>
            </b-list-group>

            <b-button variant="primary" @click="submitAnswer" :disabled="selectedIndex === null || answered">Submit</b-button>
            <b-button variant="success" @click="next">Next</b-button>
        </b-jumbotron>
    </div>
</template>

<script>
export default {
    props: {
        currentQuestion: Object,
        next: Function,
    },
    mounted(){
        console.log(this.currentQuestion)
    },
    computed: {
        answers(){
            let answers = [...this.currentQuestion.incorrent_answers]
            answers.push(this.currentQuestion.correct_answer)
            return answers;
        }
    }
}
</script>