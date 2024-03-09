<template>
    <v-card height="500" class="pa-2 " >
        <v-card-item>
        <v-card-title class="d-flex align-center pe-2 font-weight-black text-h6">
        Lista de Usuários

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
                
                height="270"
                hover
                fixed-header
        
            
            >
            <!--<template v-slot:item.id="{ item }"  class="d-none">
                <v-text>userteste01</v-text>
            </template>
            <template v-slot:item.login="{ item }" >
                <v-text>userteste01</v-text>
            </template>
            <template v-slot:item.telefone="{ item }" >
                <v-text>(27) 981767293</v-text>
            </template>
            <template v-slot:item.funcao="{ item }" >
                <v-text>admin</v-text>
            </template>-->
            <template v-slot:item.idPerfil="{ item }" >
                <v-text>P{{ item.idPerfil }}</v-text>
            </template>
            <template v-slot:item.ativoInativo="{ item }" >
                <v-switch readonly :model-value="item.ativoInativo == 'A'?true:false" :color="item.ativoInativo == 'A'?'success':'error'"></v-switch>
            </template>

            <!--<template v-slot:item.dataRegistro="{ item }" >
                <v-text>{{ formatarData(item.dataRegistro) }}</v-text>
            </template>
            <template v-slot:item.dataAtualizacao="{ item }" >
                <v-text>{{ formatarData(item.dataAtualizacao) }}</v-text>
            </template>-->

            <template v-slot:item.actions="{ item }">
                
                <div class="d-flex justify-end">
                <update :IdUser="item.id" :Username="item.name" :Useremail="item.email" Userbirthdate='2024-02-21T18:40:03.487Z'/>

                <delete :IdUser="item.id" :Username="item.name" />

               
                </div>
            </template>
          
            
            </v-data-table-virtual>
            <v-card-actions >
            
                
                <v-btn @click="refresh"   color="#1A237E" variant="flat"   prepend-icon="mdi-refresh" class="px-6 mt-2">Atualizar</v-btn>

            </v-card-actions>
            
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
    lazy: true
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
  