<template>
  <div>
    <questionStepper :currentStep="currentStep" @stepChanged="currentStep=$event"/>
    <div class="mt-4">
    <addPeople v-if="currentStep==1"/>
    <questionsForm v-if="currentStep==2"/>
  </div>
  </div>
</template>

<script>
  import addPeople from '../components/addPeople.vue'
  import questionStepper from '../components/stepper.vue'
  import questionsForm from '../components/questionsForm.vue'
  export default {
    name: 'HomePage',
    data(){
      return{
        currentStep:1
      }
    },
    
    components: {
      addPeople,
      questionStepper,
      questionsForm
    },
  }
</script>
