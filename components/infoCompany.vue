<template>
    <div class=" w-100 mb-2  rounded-sm bg-teal pa-4 elevation-4" style="height: 250px; overflow-y: hidden;">

      <div class="h-75 d-flex justify-lg-space-between">
        <div class="h-100 d-flex  align-start w-50">
          <v-img src="~/assets/logobiaco.jpeg" height="150" max-width="150" class="rounded-sm mr-8" cover></v-img>
          <div>
            <v-list color="teal" class="bg-teal pa-0 font-weight-black">
              <p class="mb-8 "><span>ID:</span><br> CL0001</p>
              <p><span class="text-caption">Empresa:</span> Grupo Biancogress</p>
              <p><span class="text-caption">Filial:</span> Serra</p>
              <p><span class="text-caption">Contrato:</span> Ativo</p> 
            </v-list>
          </div>
        </div>
        <div>
          <v-btn  color="yellow-accent-1" variant="tonal">Editar</v-btn>
        </div>
      </div>

      <div class="h-25 w-100">
        <hr>
        <div class="w-100  d-flex">        
            <v-list class="d-flex justify-space-between W-100 bg-teal " >
              <v-list-item prepend-icon="mdi-factory" class="font-weight-black text-caption"><p>Planta Fabril: <br><span>NÃO DEFINIDO</span></p></v-list-item>
              <v-list-item prepend-icon="mdi-file-sign" class="font-weight-black text-caption"><p>Tipo de Contrato: <br><span>NÃO DEFINIDO</span></p></v-list-item>
              <v-list-item prepend-icon="mdi-clipboard-text-clock" class="font-weight-black text-caption"><p>Data de Cadastro: <br><span>20/03/2022</span></p></v-list-item>
              <v-list-item prepend-icon="mdi-update" class="font-weight-black text-caption"><p>Última Atualização: <br><span>20/03/2024</span></p></v-list-item>
            </v-list>  
        </div>
      </div>
           
    </div>
</template>











 
























<!--
<v-row >

    <v-col cols="12">

    
    <v-card height="300" elevation="4">
      <v-col cols="4">
        <v-card height="200" flat>
          <v-card-item>
            <div class="d-flex justify-space-between ">
              <div class="h-100 w-100">
                <v-img src="https://www.biancogres.com.br/img/grupo-biancogres.jpg"  height="200" ></v-img>
              </div>

              <div>
                <v-card-text>
                  teste
                </v-card-text>
                
              </div>
            </div>
          </v-card-item>
        </v-card>

      </v-col>

      <v-col cols="8">
        <v-row>
          <v-col cols="12">
            <v-card height="50">
              <v-card-item>
                <v-card-actions >
                  <v-spacer></v-spacer>
                  <v-btn color="yellow-lighten-1"  variant="flat">Editar</v-btn>
                  <v-btn color="deep-orange-darken-4" variant="flat">Eliminar</v-btn>
                </v-card-actions>
              </v-card-item>
            </v-card>

          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
            <v-row>
              <v-col cols="3">
                <v-card height="100"  color="orange-darken-4" flat class="pa-2">
                      <div  class="d-flex flex-column justify-space-between align-center h-100 w-100">
                            <h1 class="text-h3 font-weight-black "> + 7.820</h1>
                            <p class="text-caption ">Anomalias Detectadas</p>
                        </div>
                    </v-card>

              </v-col>
            </v-row>
            
          </v-col>
        </v-row>
        
      </v-col>

    </v-card>
  </v-col>
    
     

            <v-card-item>
                <v-card-actions >
                  <v-spacer></v-spacer>
                  <v-btn color="yellow-lighten-1"  variant="flat">Editar</v-btn>
                  <v-btn color="deep-orange-darken-4" variant="flat">Eliminar</v-btn>
                </v-card-actions>
                <v-card-item class="pt-4 pr-4">
                  <v-row>
                    <v-col cols="3" class="">
                      <v-card height="150" elevation="10" class="pa-2">
                        <v-row>
                          <v-col cols="8">
                            <v-img src="https://www.biancogres.com.br/img/grupo-biancogres.jpg" height="150" ></v-img>

                          </v-col>
                          <v-col cols="4">
                          
                          </v-col>
                        </v-row>
                      </v-card>
                    </v-col>
                    <v-spacer></v-spacer>
                    <v-col cols="3">
                      <v-card height="100" elevation="" class="pa-2" flat>
                          <div  class="d-flex flex-column justify-space-between align-center h-100 w-100">
                            <h1 class="text-h3 font-weight-black text-purple"> + 11.780</h1>
                            <p class="text-caption text-purple-darken-4">Total Inspeções</p>
                          </div>
                      </v-card>
                    </v-col>
                    <v-col cols="3">
                      <v-card height="100"  color="orange-darken-4" flat class="pa-2">
                      <div  class="d-flex flex-column justify-space-between align-center h-100 w-100">
                            <h1 class="text-h3 font-weight-black "> + 7.820</h1>
                            <p class="text-caption ">Anomalias Detectadas</p>
                        </div>
                    </v-card></v-col>
                    <v-col cols="3">
                      <v-card height="100" elevation="4" color="teal-darken-4" class="pa-2">
                        <div  class="d-flex flex-column justify-space-between align-center h-100 w-100">
                            <h1 class="text-h3 font-weight-black "> + 4.820</h1>
                            <p class="text-caption ">Anomalias Eliminadas</p>
                        </div>
                    </v-card>
                  </v-col>
                  </v-row>
                  
                </v-card-item>

               
                
                <v-card-item>
                  <hr class="my-2"/>

                </v-card-item>



              
            </v-card-item>

   </v-row>
-->