<template>
    <div class="question-box-container">
        <b-jumbotron>
            <template #lead>
            {{ currentQuestion.question }}
            </template>

            <hr class="my-4">

            <p v-for="answer in answers" :key="answer">
                {{answer}}
            </p>

            <b-button variant="primary" href="#">Submit</b-button>
            <b-button variant="success" @click="next" href="#">Next</b-button>
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