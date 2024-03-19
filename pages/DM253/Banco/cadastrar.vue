<template>
  <div class="mt-16">
    <v-container>
    
      

      
      <v-form class="w-75 mx-auto ">
        <v-card flat>
        

          
        <v-btn prepend-icon="mdi-arrow-left-circle" to="/DM253" variant="plain" color="red-darken-4">Voltar</v-btn>
        <h1 class="text-h5 mt-4 mb-10 font-weight-bold text-cyan-darken-4" style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;">Local da Instalação</h1>
        
        <div class="h-100  bg-grey-lighten-3 pa-8 rounded-lg">
        <v-card-item  class="h-100">
        
        <v-row>
          <h1 class="text-subtitle-1 font-weight-bold px-4 mt-2">Local</h1>
          <v-col cols="12">       
            <v-text-field label="Código*" variant="solo-inverted" density="compact"></v-text-field>
          </v-col>
          <v-col cols="12">   
       
            <v-text-field label="Descrição*" variant="solo-inverted" density="compact"></v-text-field>
          </v-col>
          <v-col cols="12">   
                   
            <v-text-field label="Detalhes" variant="outlined" density="compact"></v-text-field>
          </v-col>
        </v-row>


        <v-row>
          
          <v-col cols="3">
            <p class="my-6 text-caption">Tipo de Local</p>
            <v-select
              v-model="tipoLocal"
              label="Select*"
              :items="['Elétrico', 'Mecânico']"
              variant="outlined"
              density="compact"
            ></v-select>


          </v-col>
          

          <v-col cols="5">
            <p class="my-6 text-caption">Tipo Inspeção</p>
            <v-autocomplete
            v-model="tipoInspecao"
            label="Inspeção*"
            :items="tipoLocal=='Mecânico'?inspecaoMecanica:inspecaoEletrica"
            variant="outlined"
            density="compact"
            clearable
            ></v-autocomplete>

            </v-col>

            <v-spacer></v-spacer>
            <v-col cols="2">
            <p class="my-6 text-caption">Classificação</p>
            <v-select
            
              label="ABC*"
              :items="['A', 'B', 'C']"
              variant="outlined"
              density="compact"
            ></v-select>

            </v-col>

        </v-row>
        <small class="text-caption text-medium-emphasis">* Indica campo Obrigatório</small>
      </v-card-item>
    <v-divider></v-divider>

    <v-card-actions>
      <v-spacer></v-spacer>

      <v-btn
        text="Cancelar"
        variant="plain"
        to="/DM253"
      ></v-btn>

      <v-btn
        color="primary"
        text="Salvar"
        variant="tonal"
      ></v-btn>
    </v-card-actions>

      </div>
    
    </v-card>
      </v-form>
    </v-container>
  </div>
</template>

<script setup>
import { ref } from 'vue';


definePageMeta({
  layout: 'dms',
});

const tipoLocal = ref(null);
const tipoInspecao = ref(null);

const inspecaoMecanica = ['Sensitiva', 'Análise de Vibração', 'Todas']

const inspecaoEletrica = ['Sensitiva', 'Termografia','Ultrassom' ,'Todas']

</script>