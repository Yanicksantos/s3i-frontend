<template>
    <v-app >
      <v-app-bar class="bg-índigo-escurecer-4" color="#1A237E">
       <v-app-bar-title >  
            <v-list class="d-flex bg-transparent">
                <v-list-item><v-btn icon="mdi-menu" variant="text" @click="drawer = !drawer"></v-btn></v-list-item>
            <v-list-item>DM253</v-list-item>
            </v-list> 
          
       </v-app-bar-title>
       <template #append>
            <v-list class="d-flex bg-transparent">
                <v-list-item><v-btn icon="mdi-help-circle-outline" variant="text"></v-btn></v-list-item>
                <v-list-item><v-btn variant="text" prepend-icon="mdi-exit-run" to="/usuarios">Sair</v-btn></v-list-item>
            </v-list>   
       </template>
      </v-app-bar>
      
    <v-navigation-drawer       
      :width="drawer?'300':'70'"
      class="pt-2 pb-2"
      v-model="drawer"
      temporary
    >
       
      <v-list>
        <v-list-item class="mb-4" prepend-icon="mdi-home-account">
         <v-btn variant="plain" text="Home" to="/DM253" class="text-body-2 font-weight-regular"></v-btn>
        </v-list-item>

        <div class="d-flex  align-center pl-4 mb-2"  >
          <div class="w-auto mr-4 font-weight-black " style="font-size: 12px;" v-if="drawer">Banco</div>
          <div class="w-75" ><hr></div>
        </div>




        <v-list-group value="Consultar" class="text-caption">
        <template v-slot:activator="{ props:propscadastrar }">
          <v-list-item
            v-bind="propscadastrar"
            prepend-icon="mdi-database-search"
            class="text-caption"
          >
          <v-list-item-title class="text-caption">Consultar</v-list-item-title>
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
        
      <v-list-group value="Cadastrar" class="text-caption">
        <template v-slot:activator="{ props:propsconsultar }">
          <v-list-item
            v-bind="propsconsultar"
            prepend-icon="mdi-database-plus"
            class="text-caption"
          >
          <v-list-item-title class="text-caption">Cadastrar</v-list-item-title>
        </v-list-item>

         
        </template>
        <v-list-item
            v-for="(title, i) in relatorio2"
            :key="i"
            class="text-caption"
          >
          
          <v-list-item-title class="text-caption">{{ title }}</v-list-item-title>
        </v-list-item>


      </v-list-group>






      <div class="d-flex  align-center pl-4 my-4"  >
          <div class="w-auto mr-4 font-weight-black " style="font-size: 12px;" >Planejamento</div>
          <div class="w-75" ><hr></div>
        </div>

        <v-list-item
          v-for="[icon, text, to] in links2"
          :key="icon"
          :prepend-icon="icon"
          link
          class="text-caption"
          :href="to"
        >
        <v-btn variant="plain" :text="text" :to="to" class="text-body-2 font-weight-regular"></v-btn>
      </v-list-item>
     

      <div class="d-flex  align-center pl-4 mb-2 mt-4"  >
          <div class="w-auto mr-4 font-weight-black " style="font-size: 12px;" >Check-list de Inspeção</div>
          <div class="w-75" ><hr></div>
        </div>

        <v-list-item
          prepend-icon="mdi-database-settings"
          link
          class="text-caption"
          
        >
        <v-list-title>A carregar...</v-list-title>
      </v-list-item>

      <v-list-item
          prepend-icon="mdi-list-status"
          link
          class="text-caption"
          
        >
        <v-list-title>Acompanhamento</v-list-title>
      </v-list-item>
    
      </v-list>
      </v-navigation-drawer>
      
      <slot />

    </v-app>
   
</template>



<script setup>
import { ref } from 'vue'

const drawer = ref(false)





const links2 = [
  ['mdi-account-search', 'Cadastrar', '/DM253/planejamento'],
  ['mdi-text-search-variant', 'Listar', '/DM253/planejamento'],
]

const relatorio=  ['Sensitiva', 'Análise de Vibração']

const relatorio2=  ['Sensitiva', 'Análise de Vibração']



</script>



  