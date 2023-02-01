<template>
    <div>
        <div v-for="question in getQuestions" :key="question.id">
            <questionBox :question="question" :answer="getQuestionAnswers.find(answer => answer.id == question.id)?.answer || ''" @answerChange="answerChange(question.id, $event )" />
        </div>
    </div>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'

    import questionBox from './questionBox.vue'
export default {
    name:"questionsForm",
    components:{questionBox},
    computed:{
        ...mapGetters(["getQuestionAnswers","getQuestions"])
    },
    methods:{
        ...mapActions(["setQuestionAnswer"]),

        answerChange(id, answer){
            this.setQuestionAnswer({id, answer})
        },
        
    },
}
</script>

<style>

</style>