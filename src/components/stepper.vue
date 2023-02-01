<template>
  <div>
    <v-stepper non-linear :value="step" @change="$emit('stepChanged',$event)">
      <v-stepper-header>
        <v-stepper-step
          editable
          step="1"
        >
          הוסף אנשים
        </v-stepper-step>

        <v-divider></v-divider>

        <v-stepper-step
          editable
          step="2"
        >
          שאלות
        </v-stepper-step>

        <v-divider></v-divider>

        <v-stepper-step
          step="3"
          editable
        >
          הצעות והמלצות
        </v-stepper-step>
      </v-stepper-header>
    </v-stepper>
  </div>
</template>

<script>
export default {
    name:"questionStepper",
    prop:{
      currentStep:{required: true}
    },
    computed:{
      step(){
        // vue raises an error without this.... yuck
        return this.currentStep || 1
      }
    }
}
</script>

<style>

</style>