<template>
<div class="h-100 mt-16 px-4">

        <v-row  class="mt-1">
            <v-col cols="2" >
                <v-card height="135" flat>
                    <img src="~/assets/logo.jpeg" alt="" class="obj h-100 w-100">
                </v-card>
                    
            </v-col>

            <v-col cols="4">
                <v-card variant="outlined" height="135" elevation="4">
                    
                </v-card>
                
            </v-col>

            <v-col cols="3"  >
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
                
            </v-col>

            <v-col cols="3"  >
                <v-card variant="outlined"  elevation="4" height="135">
                        
                </v-card>
                
            </v-col>

        </v-row>
        <v-row>
            <v-col cols="12">
            <v-card height="350" variant="outlined">
                <v-row class="px-4 pb-2 pt-8 ">
            
                    <v-col cols="3">
                        <v-card height="300" variant="outlined" elevation="6">

                        </v-card>

                    </v-col>
                        <v-col cols="6">
                        <v-card height="300" variant="outlined" elevation="6">

                        </v-card>

                    </v-col>
                        <v-col cols="3">
                        <v-card height="300" variant="outlined" elevation="6">

                        </v-card>

                    </v-col>
                </v-row>

            </v-card>

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