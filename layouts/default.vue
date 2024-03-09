<template>
    <v-app id="inspire">
        
      <v-app-bar height="50" class="px-auto py-2 elevation-1">
        <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
            <v-app-bar-title >
                <nuxt-link to="/">
                    <v-img src="https://predengenharia.vercel.app/img/Headers/Logomarca-Pred-Engenharia-1536x319.png"  max-width="100"></v-img>              
                </nuxt-link>
            </v-app-bar-title>

            
         
            <v-list class="d-flex mr-10">
              <v-list-item><v-btn variant="flat" color="indigo-darken-4" size="small">HelpDesk</v-btn> </v-list-item>
            </v-list>

        <template v-slot:append>
          <v-list class="px-6 d-flex justify-lg-space-between align-center">

          <v-btn>
            <v-badge :content="5" color="error">
            <v-icon icon="mdi-bell-cog" ></v-icon>
          </v-badge>

          </v-btn>
          
          
          <v-avatar
              size="36px"
              class=" mx-6"
            >
              <v-img
                alt="Avatar"
                src="https://avatars0.githubusercontent.com/u/9064066?v=4&s=460"
              ></v-img>
          </v-avatar>

          </v-list>
        </template>
    </v-app-bar>

    <v-navigation-drawer       
      :width="drawer?'300':'50'"
      class="pt-6"
      
    >
       
      <v-list>
        <v-list-item prepend-icon="mdi-home-account" class="mb-6" link >
          <v-list-item-title v-if="drawer" >Home</v-list-item-title>
        </v-list-item>

        <div class="d-flex  align-center pl-4 mb-2" v-if="drawer" >
          <div class="w-auto mr-4 font-weight-black " style="font-size: 12px;">Clientes</div>
          <div class="w-50" ><hr></div>
        </div>

        <v-list-item
          v-for="[icon, text] in links"
          :key="icon"
          :prepend-icon="icon"
          link
          class="text-caption"
          
        >
        <v-list-title v-if="drawer" >{{ text }}</v-list-title>
      </v-list-item>

      <div class="d-flex  align-center pl-4 my-4" v-if="drawer" >
          <div class="w-auto mr-4 font-weight-black " style="font-size: 12px;">Serviços e Produtos</div>
          <div class="w-25" ><hr></div>
        </div>

        <v-list-item
          v-for="[icon, text] in links2"
          :key="icon"
          :prepend-icon="icon"
          link
          class="text-caption"
        >
        <v-list-title v-if="drawer" >{{ text }}</v-list-title>
      </v-list-item>
      <v-list-group value="Relatorio de Inspeção" class="text-caption">
        <template v-slot:activator="{ props }">
          <v-list-item
            v-bind="props"
            prepend-icon="mdi-chart-bar"
            class="text-caption"
          >
          <v-list-item-title class="text-caption">Relatorio de Inspeção</v-list-item-title>
        </v-list-item>

         
        </template>
        <v-list-item
            v-for="(title, i) in relatorio"
            :key="i"
            class="text-caption"
          >
          <v-list-item-title class="text-caption">{{ title }}</v-list-item-title>
        </v-list-item>


      </v-list-group>
    
      </v-list>
      </v-navigation-drawer>
        <slot />
    </v-app>
  </template>

<script setup>
import { ref } from 'vue'

const drawer = ref(true)



const links = [
  
  ['mdi-list-status', 'Listar'],
  ['mdi-account-plus', 'Cadastrar'],
  ['mdi-account-search', 'Consultar'],
]

const links2 = [
  ['mdi-family-tree', 'Arvore Lógica de Planta Fabril'],
  ['mdi-file-tree', 'Árvore de falha par MCI'],
  ['mdi-alphabetical-variant', 'Matriz das Criticidades ABC'],
]

const relatorio=  ['Instalações Eletricas', 'Sistemas de Fluidos Gasosos', 'Mecânicas e Estrutural(ES)']



</script>

  