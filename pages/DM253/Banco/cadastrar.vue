<template>
  <div class="mt-16">
    <v-container>
    
      

      
      <v-form class="w-75 mx-auto ">
        <v-card flat>
        

          
        <v-btn prepend-icon="mdi-arrow-left-circle" to="/DM253" variant="plain" color="teal-darken-4">Voltar</v-btn>
        <h1 class="text-h5 mt-4 mb-10 font-weight-bold text-cyan-darken-4" style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;">Local da Instalação</h1>
        
        <div class="h-100  bg-grey-lighten-3 pa-8 rounded-lg">
        <v-card-item  class="h-100">


        
        <v-row>
          <h1 class="text-subtitle-1 font-weight-bold px-4 mt-2">Local</h1>
          <v-col cols="12">
            <v-row>
              <v-col cols="4">
                <v-text-field label="Nivel1*" variant="solo-inverted" density="compact"></v-text-field>
              </v-col>
              <v-col cols="4">
                <v-text-field label="Nivel2" variant="solo-inverted" density="compact"></v-text-field>
              </v-col>
              <v-col cols="4">
                <v-text-field label="Nivel3" variant="solo-inverted" density="compact"></v-text-field>
              </v-col>
              <v-col cols="4">
                <v-text-field label="Nivel4" variant="solo-inverted" density="compact"></v-text-field>
              </v-col>
              <v-col cols="4">
                <v-text-field label="Nivel5" variant="solo-inverted" density="compact"></v-text-field>
              </v-col>
              <v-col cols="4">
                <v-text-field label="Nivel6" variant="solo-inverted" density="compact"></v-text-field>
              </v-col>
              <v-col cols="3" >
                <v-text-field label="POS*" variant="solo-inverted" density="compact"></v-text-field>
              </v-col>
            </v-row>
          </v-col>
          <v-col cols="12">   
            <p class="mb-2 text-caption px-4">prévia Tag</p>    
            <v-text-field  variant="solo-inverted" density="compact" disabled value="RKF01-CAA01-EV01"></v-text-field>
          </v-col>
          <v-col cols="12">   
       
            <v-text-field label="Descrição*" variant="solo-inverted" ></v-text-field>
          </v-col>
          <v-col cols="12">   
                   
            <v-text-field label="Detalhes" variant="outlined" ></v-text-field>
          </v-col>
        </v-row>


        <v-row>

          <v-col cols="5" >
            <p class="my-6 text-caption">Tipo Local</p>
            <div class="d-flex">
              <v-checkbox 
              v-model="selectedEletrico"
              :disabled="selectedMecanico"
              label="Elétrico"
              value="E"
              ></v-checkbox>


              <v-checkbox 
              v-model="selectedMecanico"
              :disabled="selectedEletrico"
              label="Mecânico"
              value="M"
              ></v-checkbox>  
            </div>
                  
          </v-col>
          
          <v-col cols="4">
            <p class="my-6 text-caption text-center">Tipo de Inspeção</p>
            <v-text v-if="selectedEletrico" class="text-center">
              <v-chip  text="Sensitiva"  size="small" class="mr-2"></v-chip>
              <v-chip  text="Termografia"  size="small" class="mr-2"></v-chip>
              <v-chip  text="Ultrassom"  size="small" ></v-chip>
            </v-text>

            <v-text v-else-if="selectedMecanico" class="text-center">
              <v-chip  text="Sensitiva"  size="small" class="mr-2"></v-chip>
              <v-chip  text="Análise de Vibração"  size="small" ></v-chip>
            </v-text>


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

const selectedEletrico = ref (false)
const selectedMecanico = ref (false)
</script>