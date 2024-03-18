<template>
    <v-card height="500" class="pa-2 " >
        <v-card-item>
        <v-card-title class="d-flex align-center pe-2 font-weight-black text-h6">
        Lista de Usuários  
        <v-tooltip text="Atualizar">
            <template v-slot:activator="{ props }">
                <v-btn 
                @click="refresh"  size="small"  color="#1A237E" variant="text"   icon="mdi-refresh" class="ml-4"
                v-bind="props"
                ></v-btn>
            </template>
        </v-tooltip>
        <v-spacer></v-spacer>
            <modal/>
     
       
        </v-card-title>

        </v-card-item>

        <v-card-item>
        <v-row>
            <v-col cols="4">
                <v-text-field
                    v-model="search"
                    prepend-inner-icon="mdi-magnify"
                    density="compact"
                    label="Search"
                    single-line
                    flat
                    hide-details
                    size="small"
                    variant="outlined"
                
                ></v-text-field>
            </v-col>
            
            
            <v-spacer></v-spacer>
        
            <v-col cols="3">
                <v-card height="50" elevation="" class="pa-2" flat variant="tonal">
                    <div  class="d-flex flex-column justify-space-between align-center h-100 w-100">
                        <h1 class="text-caption font-weight-black text-purple"> 745 </h1>
                        <p class="text-caption text-purple-darken-4">Usuarios Cadastrados</p>
                    </div>
                </v-card>
                </v-col>
            
                <v-col cols="3">
                <v-card height="50"  color="teal-darken-4" class="pa-2" flat variant="tonal">
                    <div  class="d-flex flex-column justify-space-between align-center h-100 w-100">
                        <h1 class="text-caption font-weight-black "> 225</h1>
                        <p class="text-caption ">Usuarios Ativos</p>
                    </div>
                </v-card>
            </v-col>
        </v-row>

        </v-card-item>
        
        <v-card-item v-if="pending">
            <v-progress-linear indeterminate 
            absolute
            bottom
            ></v-progress-linear>
        </v-card-item>

        <v-card-item v-else>
            <v-data-table-virtual
                :headers="headers"
                :items="usersi"
                :search="search"
                density="compact"
                size="x-small"
                height="300"
                hover
                fixed-header
                class="text-caption"
        
            
            >
        
            <template v-slot:item.idPerfil="{ item }" >
                <v-chip variant="outlined" :color="item.idPerfil==2? 'green-darken-4':'yellow-accent-4'"  size="small">
                    P{{ item.idPerfil }}
                </v-chip>
            </template>

            <template v-slot:item.ativoInativo="{ item }" >
                <v-chip  :text="item.ativoInativo=='A'? 'Ativo':'Inativo'" variant="outlined" :color="item.ativoInativo=='A'? 'green-darken-4':'red-accent-4'"  size="small" ></v-chip>
            </template>


            <template v-slot:item.actions="{ item }">             
                <div class="d-flex justify-end">
                   <detalhes />
                <!--<update :IdUser="item.id" :Username="item.name" :Useremail="item.email" Userbirthdate='2024-02-21T18:40:03.487Z'/>

                <delete :IdUser="item.id" :Username="item.name" />-->
                </div>
            </template>    

            </v-data-table-virtual>   
        </v-card-item>

    </v-card>
 
            
</template>



<script setup>
 import { format } from 'date-fns';
 import { ref } from 'vue'


    const search = ref('');
    const model = ref (false);

    const { data: usersi, pending, refresh } = await useFetch("https://inspec.up.railway.app/api/Usuarios/GetUsuarios", {
    method: "GET",
    headers: {
        "content-type": "application/json"
    },
    });

    const formatarData = (data) => {
        return format(new Date(data), 'dd-MM-yyyy hh:mm:ss a');
    };

 const headers = [
        //{ align: 'start', key:'id', title: 'Id',},
        { key: 'nome', title: 'Nome',},
        { key: 'login', title: 'Login' },
        { key: 'email', title: 'E-mail' },
        { key: 'telefone', title: 'telefone',},     
        { key: 'idPerfil', title: 'Cargo',},
        { key: 'ativoInativo', title: 'status',},
        //{ key: 'dataRegistro', title: 'Cadastrado', },
       // { key: 'dataAtualizacao', title: 'Ult.Atualização', },
        { key: 'actions', title: '',  },

    ]


  </script>
  