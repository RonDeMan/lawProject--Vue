<template>
  <div>
        <h3>{{ question.text }}: {{ question.required ? '*': "" }}</h3>
        <component :value="answer" :is="question.type" :label="question.label"  @change="$emit('answerChange',$event)"
                   :prefix="question.prefix" :items="questionItems" :item-value="itemValue">
                   <template slot="item" slot-scope="data">
                      {{ itemText(data.item) }}
                    </template>
                   <template slot="selection" slot-scope="data">
                    {{ itemText(data.item) }}
                    </template>
 </component>
  </div>
</template>

<script>
import { VTextField,VSelect } from 'vuetify/lib'
import { mapGetters } from 'vuex';
export default {
    name:"questionBox",
    props:["question", "answer"],
    components:{
      VTextField,
      VSelect
    },

    computed:{
      ...mapGetters(["getPeopleForSelect","getNicknames"]),

      questionItems(){
        if (!this.question.items) return []
        switch (this.question.items) {
          case 'people':
            return this.getPeopleForSelect

        
          default:
            return []
        }
      },

      itemValue(){
        switch (this.question.items) {
          case 'people':

            return 'id' 

        
          default:
            return ''
        }
      },

      
    },
    methods:{
      itemText(item){
        switch (this.question.items) {
          case 'people':

            return item.nickname == 0 ? `${item.firstName} ${item.lastName}` : this.getNicknames[item.nickname].text 

        
          default:
            return ''
        }
      },
      
    }
}
</script>

<style>

</style>