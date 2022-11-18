<template>
  <div>
    <v-col
      cols="12"
      sm="6"
    >
      <v-text-field
        v-model="campoImput"
        label="Qual sua tarefa?"
        outlined
        clearable
        @keyup.enter="handleAddTarefa"
      ></v-text-field>
    </v-col>

    <v-list
      flat
      subheader
    >
      <v-list-item-group
        multiple
        active-class=""
      >

      <div
      v-for="tarefa, index in $store.state.tarefas"
      :key="index"
      >
        <Tarefa
        :tarefa="tarefa"
        />
      </div>

      </v-list-item-group>
    </v-list>
  </div>
</template>

<script>
import Tarefa from '../components/tarefas/Tarefa.vue'  
  
export default {
    name: 'HomeVue',

    components: {
      Tarefa
    },
    data(){
      return{
        campoImput: null,
      }
    },
    methods:{
      handleAddTarefa(){
        this.$store.commit('adicionaTarefa', this.campoImput)
        this.campoImput = null;
      }
    }
  }
</script>
