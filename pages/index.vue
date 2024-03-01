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
  
      <v-navigation-drawer v-model="drawer" color="blue-grey-darken-4" width="200" v-if="true">
       
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
        
        <info-company />

         <v-row>
            
            <v-col cols="10">
              <table-users />
            </v-col>
            <v-col cols="2">
               <Details />
            </v-col>
        </v-row>
        </v-container>
      </v-main>
    </v-app>
  </template>
  
  <script setup>
    import { ref } from 'vue'


    const cards = ['Today', 'Yesterday']
    const links = [
      ['mdi-inbox-arrow-down', 'Inbox'],
      ['mdi-send', 'Send'],
      ['mdi-delete', 'Trash'],
      ['mdi-alert-octagon', 'Spam'],
    ]
  
    const drawer = ref(null)

  </script>
  
