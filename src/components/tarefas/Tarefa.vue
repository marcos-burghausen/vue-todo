<template>
   <div>
      <v-list-item
         :class="{'blue lighten-4':tarefa.concluido}"
         @click="changeValue()"
      >
         <template v-slot:default="{}">
            <v-list-item-action>
               <v-checkbox :input-value="tarefa.concluido"></v-checkbox>
            </v-list-item-action>
            <v-list-item-content
               :class="{'text-decoration-line-through': tarefa.concluido}"
            >
               <v-list-item-title>{{ tarefa.titulo }}</v-list-item-title>
            </v-list-item-content>
            <v-list-item-action>
               <TarefaMenu :tarefa="tarefa"/>
            </v-list-item-action>
         </template>
      </v-list-item>
      <v-divider/>
   </div>
</template>

<script>
import TarefaMenu from './TarefaMenu.vue'
   export default {
   components: { TarefaMenu },
   name: 'TarefaVue',
   props:['tarefa'],
   data(){
      return{
         tarefaR: this.tarefa
      }
   },
   methods: {
      changeValue() {
         this.tarefaR.concluido = !this.tarefaR.concluido
      },
      handelRemoveTarefa(id){
         this.$store.commit('removeTarefa', id)
      }
   }
   }
</script>

<style>

</style>