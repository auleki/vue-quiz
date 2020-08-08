<template>
    <div>
        <b-jumbotron header="Quick Quiz">
            <template v-slot:lead>
                {{ currentQuestion.question }}
            </template>

            <!-- <hr class="my-4"> -->
            <b-list-group>
                <b-list-group-item 
                    v-for="(answer, index) in answers" 
                    :key="index"
                    @click.prevent="selectedAnswer(index)"
                >
                    {{ answer }}    
                </b-list-group-item>
                
            </b-list-group>

            <b-button variant="primary" href="#">Submit</b-button>
            <b-button @click="next" variant="success" href="#">Next Question</b-button>
        </b-jumbotron>
    </div>
</template>

<script>
export default {
    props: {
        currentQuestion: Object,
        next: Function
    },
    methods: {
        selectedAnswer(index) {
            console.log(index)
        }
    },
    data: function () {
        return {
            selectedIndex: null,
            shuffledAnswers: []
        }
    },
    computed: {
        answers() {
            let answers = [...this.currentQuestion.incorrect_answers]
            answers.push(this.currentQuestion.correct_answer)
            return answers
        }
    }

}
</script>


<style scoped>
    .list-group {
        margin-bottom: 20px;
    }

    .btn {
        margin: 0 15px;
    }
</style>