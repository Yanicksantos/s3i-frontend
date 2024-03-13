<template>
<div class="h-100 mt-16 px-4">

        <v-row  class="mt-1">
            <v-col cols="2" >
                <v-card height="135" flat>
                    <img src="~/assets/logo.jpeg" alt="" class="obj h-100 w-100">
                </v-card>
                    
            </v-col>

            <v-spacer></v-spacer>
            <v-col cols="4">
               
                    <div style="position: relative; border: 1px solid black;" class="w-100 h-100 rounded elevation-4 ">
                        <p style="position: absolute;  top: -10px; z-index: 1; left: 20px;" class=" text-caption bg-white px-2">Escopo</p>
                    </div>
            </v-col>

           <!-- <v-col cols="3"  >
                <v-card  height="135" elevation="4" variant="outlined">
                    <v-space></v-space>
                    <v-card-text>
                            <v-select
                            bg-color ='grey-lighten-4'
                            label="Anomalia Consolidadas"
                            :items="['Sensitiva', 'Vibração', 'Analitica']"
                            variant="outlined"
                            density="compact"
                            clearable
                            persistent-hint
                            ></v-select>

                            <v-select
                        
                            bg-color ='grey-lighten-4'
                            label="Outros Relatórios"
                            :items="['Anomalias Pendentes', 'Anomalias detectadas x concluídas', 'Cumprimento das rotinas', 'Supervisão Diária do Sistema', 'Performance das inspeções']"
                            variant="outlined"
                            density="compact"
                            color='black'
                            clearable
                            class="text-caption"
                            persistent-hint
                            ></v-select>

                    </v-card-text>
                    
                            
                    
                </v-card>
                
            </v-col>-->

            <v-col cols="3"  >
                <div style="position: relative; border: 1px solid black;" class="w-100 h-100 rounded elevation-4 ">
                        <p style="position: absolute;  top: -10px; z-index: 1; left: 20px;" class="bg-white px-2 text-caption">Responsaveis Técnicos</p>
                </div>
                
            </v-col>

        </v-row>
        <v-row>
            <v-col cols="12">                
                <div style="position: relative; border: 1px solid black; height: 350px;" class="w-100 rounded elevation-4 ">
                    <p style="position: absolute;  top: -10px; z-index: 1; left: 20px;" class="bg-white px-2 text-caption">Relatórios Estáticos</p>
                    
                    <v-row class="px-4 pb-2 pt-8 ">
                
                        <v-col cols="3">
                            <div style="position: relative; border: 1px solid black; height: 300px;" class="w-100  elevation-4 ">
                                <p style="position: absolute;  top: -10px; z-index: 1; left: 20px;" class="bg-white px-2 text-caption">Situação da Inspeção</p>
                            </div>
                        </v-col>


                        <v-col cols="6">
                            <div style="position: relative; border: 1px solid black; height: 300px;" class="w-100   elevation-4 ">
                                <p style="position: absolute;  top: -10px; z-index: 1; left: 20px;" class="bg-white px-2 text-caption">Perigômetro</p>
                            </div>
                        </v-col>

                        <v-col cols="3">
                            <div style="position: relative; border: 1px solid black; height: 300px;" class="w-100   elevation-4 ">
                                <p style="position: absolute;  top: -10px; z-index: 1; left: 20px;" class="bg-white px-2 text-caption">Situação das anomalias</p>
                            </div>

                        </v-col>
                    </v-row>
                </div>  
            </v-col>
        </v-row>

        <div class="">
            <p>DM253® - Todos os direitos reservados a Pred Engenharia Ltda.</p>
        </div>

</div>          
    
</template>
    
 

<script setup>
definePageMeta({
  layout: 'dms',
});

</script>

<style >
    .obj{
        object-fit: contain;
    }
</style>