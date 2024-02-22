<template>
    <v-app id="inspire">


      <v-app-bar :elevation="2">
            <v-app-bar-title >
                <nuxt-link to="/">
                    <v-img src="https://predengenharia.vercel.app/img/Headers/Logomarca-Pred-Engenharia-1536x319.png"  max-width="120"></v-img>              
                </nuxt-link>

           


            </v-app-bar-title>

            
         
            <v-list class="d-flex mr-10">
              <v-list-item>Árvore Lógica</v-list-item>
              <v-list-item>HelpDesk</v-list-item>
            </v-list>

        <template v-slot:append>
          <v-list class="px-6 d-flex justify-lg-space-between align-center">

          
          <v-badge :content="5" color="error">
            <v-icon icon="mdi-bell-cog" ></v-icon>
          </v-badge>

          <v-avatar
              size="36px"
              class=" mx-6"
            >
              <v-img
                alt="Avatar"
                src="https://avatars0.githubusercontent.com/u/9064066?v=4&s=460"
              ></v-img>
            </v-avatar>
            <span class="font-weight-thin">PedroSouza54, <span class="font-weight-black">Admin</span> </span>
          </v-list>
        </template>
    </v-app-bar>
  
      <v-navigation-drawer v-model="drawer" color="blue-grey-darken-4" width="200">
       
        <v-list>
          <v-list-item
            v-for="[icon, text] in links"
            :key="icon"
            :prepend-icon="icon"
            :title="text"
            link
          ></v-list-item>
        </v-list>
      </v-navigation-drawer>
  
      <v-main class="bg-grey-lighten-1">
        <v-container
          class="py-8 px-6"
          fluid
        >



         <v-row>
            <v-col cols="12">
                <v-card height="250" elevation="1">
                  <v-card-item>
                      <v-card-actions>
                        <v-spacer></v-spacer>
                        <v-btn color="yellow-lighten-1"  variant="flat">Editar</v-btn>
                        <v-btn color="deep-orange-darken-4" variant="flat">Eliminar</v-btn>
                      </v-card-actions>
                    
                  </v-card-item>

                </v-card>
            </v-col>
         </v-row>




         <v-row>
            <v-col cols="3">
                <v-card elevation="8" height="500">
                                                      
                        <v-card-actions> 
                            <v-card-title>Informações</v-card-title>
                            <v-spacer></v-spacer>
                            <v-btn icon="mdi-plus"></v-btn>
                        </v-card-actions>
                        <v-card-item>
                            <v-card-text> hakhdfkfdfdafdfefydff df df fdydfdkfdddd dgfgfghdkdfhfkd</v-card-text>
                        <hr/>
                        <v-card-text>hakhdfkfdfdafdfefydff df df fdydfdkfdddd dgfgfghdkdfhfkd</v-card-text>
                        
                        <hr/>
                        <v-card-text>hakhdfkfdfdafdfefydff df df fdydfdkfdddd dgfgfghdkdfhfkd</v-card-text>
                        

                        </v-card-item>
                   
                        
                   

                </v-card>
            </v-col>
            <v-col cols="9">
                <v-card elevation="8" height="500">
                  <v-card-item>
                    <v-card-title class="d-flex align-center pe-2">
                    Lista de Usuários

                    <v-spacer></v-spacer>

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
                    </v-card-title>

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
                           
                            height="350"
                            hover
                            fixed-header
                            show-select
                            select-strategy="single"
                       
                        >
                        </v-data-table-virtual>
                        <v-btn @click="refresh" class="mt-8"  color="#1A237E">Atualizar</v-btn>
                    </v-card-item>

                </v-card>
            </v-col>
            
        </v-row>
        </v-container>
      </v-main>
    </v-app>
  </template>
  
  <script setup>
    import { ref } from 'vue'
    import { format } from 'date-fns';

    const search = ref('');

    const cards = ['Today', 'Yesterday']
    const links = [
      ['mdi-inbox-arrow-down', 'Inbox'],
      ['mdi-send', 'Send'],
      ['mdi-delete', 'Trash'],
      ['mdi-alert-octagon', 'Spam'],
    ]
  
    const drawer = ref(null)

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

   /* const filterOnlyCapsText = (value, query, item) => {
        return value != null &&
          query != null &&
          typeof value === 'string' &&
          value.toString().toLocaleUpperCase().indexOf(query) !== -1
      }
      onMounted(() => {
    // A requisição será feita automaticamente quando o componente for montado
    refresh();
  });*/

 const headers = [
            {
              align: 'start',
              key: 'name',
              title: 'Nome',
            },
            { key: 'email', title: 'E-mail' },
            { key: 'birthdate', title: 'Aniversário' }
    ]


  </script>
  
