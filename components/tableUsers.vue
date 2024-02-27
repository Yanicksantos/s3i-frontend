<template>
    <v-card elevation="10" height="750" class="pa-2" color="grey-lighten-2">
        <v-card-item>
        <v-card-title class="d-flex align-center pe-2 font-weight-black text-h5">
        Lista de Usuários

        <v-spacer></v-spacer>
        <modal/>
       
        </v-card-title>

        </v-card-item>

        <v-card-item>
        <v-row>
            <v-col cols="5">
                <v-text-field
                    v-model="search"
                    prepend-inner-icon="mdi-magnify"
                    density="compact"
                    label="Search"
                    single-line
                    flat
                    hide-details
                    variant="solo-filled"
                
                ></v-text-field>
            </v-col>
            
            
            <v-spacer></v-spacer>
        
            <v-col cols="3">
                <v-card height="100" elevation="" class="pa-2" flat variant="tonal">
                    <div  class="d-flex flex-column justify-space-between align-center h-100 w-100">
                        <h1 class="text-h3 font-weight-black text-purple"> 745 </h1>
                        <p class="text-caption text-purple-darken-4">Usuarios Cadastrados</p>
                    </div>
                </v-card>
                </v-col>
            
                <v-col cols="3">
                <v-card height="100"  color="teal-darken-4" class="pa-2" flat variant="tonal">
                    <div  class="d-flex flex-column justify-space-between align-center h-100 w-100">
                        <h1 class="text-h3 font-weight-black "> 225</h1>
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
                :sort-by="[{ key: 'id', order: 'asc' }]"
                height="450"
                hover
                fixed-header
        
            
            >
            <template v-slot:item.login="{ item }" >
                <v-text>userteste01</v-text>
            </template>
            <template v-slot:item.telefone="{ item }" >
                <v-text>(27) 981767293</v-text>
            </template>
            <template v-slot:item.funcao="{ item }" >
                <v-text>admin</v-text>
            </template>
            <template v-slot:item.status="{ item }" >
                <v-switch v-model="item.id" readonly ></v-switch>
            </template>

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

    const { data: usersi, pending, refresh } = await useFetch("https://usuarioapi.up.railway.app/api/Users/GetUsers", {
    method: "GET",
    headers: {
        "content-type": "application/json"
    },
    lazy: true
    });

    const formatarData = (data) => {
        return format(new Date(data), 'dd-MM-yyyy');
    };

 const headers = [
            { align: 'start', key:'id', title: 'Id',},
            { key: 'name', title: 'Nome',},
            { key: 'login', title: 'Login' },
            { key: 'email', title: 'E-mail' },
          //  { key: 'birthdate', title: 'Aniversário' },
          { title: 'telefone', key: 'telefone',},
          { title: 'Perfil', key: 'funcao',},
            { title: 'Status', key: 'status',},
            { title: '', key: 'actions', },

    ]


  </script>
  