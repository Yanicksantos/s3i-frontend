<template>
    <div class="mt-16">
        <v-container>
        <v-form class="w-75 mx-auto">
            <v-card flat>
        <v-btn prepend-icon="mdi-arrow-left-circle" to="/DM253" variant="plain" color="teal-darken-4">Voltar</v-btn>
  
        <h1 class="text-h5 mt-4 mb-10 font-weight-bold text-cyan-darken-4" style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;">Planejamento da inspeção</h1>


        <div class="h-100  bg-grey-lighten-3 pa-8 rounded-lg">
         <v-card-item  class="h-100">
        <!--CLIENTES-->
        <div class="mt-2 ">
            <h1 class="text-subtitle-1 font-weight-bold ">Dados do Cliente</h1>
            <v-row>
                <v-col cols="5">
                    <p class="my-4 text-caption">Cliente</p>
                    <v-text-field label="Adicione o nome do Cliente" variant="outlined" density="compact"></v-text-field>
                </v-col>
                <v-col cols="5">
                    <p class="my-4 text-caption">Engenheiro Responsavél </p>
                    <v-text-field label="Responsavél" variant="outlined" density="compact"></v-text-field>
                </v-col>
                <v-col cols="2">
                    <p class="my-4 text-caption">Ordem de Serviço</p>
                    <v-text-field label="N° Ordem" variant="outlined" density="compact"></v-text-field>
                </v-col>
            </v-row>
        </div>

        <!--INSPECTOR-->
        <div class="mt-4">
            
            <v-row>
                <v-col cols="6">
                    <h1 class="text-subtitle-1 font-weight-bold mb-6">Dados do Inspector</h1>
                    <v-row>
                        
                        <v-col cols="7">
                        <p class="text-caption mb-4">Inspector</p>
                        <v-autocomplete
                            label="Inspector"
                            :items="['Ozorio', 'Edvan', 'Pedro', 'Beltrano']"
                            variant="outlined"
                            density="compact"
                            clearable
                            hide-details
                            single-line
                            ></v-autocomplete>
                        </v-col>
                         
                        <v-col cols="5">
                            <p class="text-caption mb-4">CREA/CFT</p>
                            <v-text-field label="CREA/CFT" variant="outlined" density="compact"
                            hide-details
                            single-line
                            ></v-text-field>
                        </v-col>
                    </v-row>             

                </v-col>
                <v-col cols="6">
                    <h1 class="text-subtitle-1 font-weight-bold mb-6">Dados do Analista</h1>
                    <v-row>
                        
                        <v-col cols="7">
                        <p class="text-caption mb-4">Analista</p>
                        <v-autocomplete
                            label="Analista"
                            :items="['Ozorio', 'Edvan', 'Pedro', 'Beltrano']"
                            variant="outlined"
                            density="compact"
                            clearable
                            hide-details
                            single-line
                            ></v-autocomplete>
                        </v-col>
                         
                        <v-col cols="5">
                            <p class="text-caption mb-4">CREA/CFT</p>
                            <v-text-field 
                            label="CREA/CFT" variant="outlined" density="compact" 
                            hide-details
                            single-line
                            ></v-text-field>
                        </v-col>
                    </v-row>             

                </v-col>               
            </v-row>
        </div>

        <!-- Aparelho de Vibração -->

        <div class="mt-8">
            
            <v-row>

                <v-col cols="12">
                    <h1 class="text-subtitle-1 font-weight-bold mb-8">Dados do Aparelho de Vibração</h1>
                    <v-row>
                        <v-col cols="3">
                            <v-text-field label="Fabricante" variant="solo-inverted" density="compact"></v-text-field>
                        </v-col>
                        <v-col cols="3">
                            <v-text-field label="Modelo" variant="solo-inverted" density="compact"></v-text-field>
                        </v-col>
                        <v-col cols="2">
                            <v-text-field label="S/N" variant="solo-inverted" density="compact"></v-text-field>
                        </v-col>
                        <v-col cols="4">
                            <v-text-field label="Laudo de Fabricação" variant="solo-inverted" density="compact"></v-text-field>
                        </v-col>
                    </v-row>
                     
               
                </v-col>
                <!-- Programação -->
                <v-col cols="6">
                    <h1 class="text-subtitle-1 font-weight-bold mb-8">Programação</h1>
                    <v-row>
                        <v-col cols="6">
                            <v-text-field
                            label="Inicio*"
                            type="date"
                            variant="outlined"
                            density="compact"
                            
                            ></v-text-field>
                        </v-col>
                        <v-col cols="6">
                            <v-text-field
                            label="Término*"
                            type="date"
                            variant="outlined"
                            density="compact"
                            
                            ></v-text-field>
                        </v-col>
                    </v-row>
                </v-col>
                
            </v-row>

        </div>
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
definePageMeta({
  layout: 'dms',
});

</script>