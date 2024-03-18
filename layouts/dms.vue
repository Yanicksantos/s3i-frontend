<template>
    <v-app >
      <v-app-bar class="bg-índigo-escurecer-4" color="#1A237E">
       <v-app-bar-title >  
            <v-list class="d-flex bg-transparent">
                <v-list-item><v-btn icon="mdi-menu" variant="text" @click="drawer = !drawer"></v-btn></v-list-item>
            <v-list-item class="text-caption font-weight-black">DM253 - SISTEMA DE GERAÇÃO DE RELATÓRIOS DE INSPEÇÃO MECÂNICA E ESTRUTURAL</v-list-item>
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
      class="pt-2 pb-2 px-2"
      v-model="drawer"
      temporary
    >
       
      <v-list>
        <v-list-item class="mb-4" prepend-icon="mdi-home-account">
         <v-btn variant="text" text="Home" to="/DM253" class="text-caption font-weight-regular"></v-btn>
        
        </v-list-item>

        <div>

        
        <div class="d-flex  align-center pl-4 mb-2"  >
          <div class="w-auto mr-4 font-weight-black " style="font-size: 12px;" v-if="drawer">Banco</div>
          <div class="w-75" ><hr></div>
        </div>

        
        <v-list-item
        prepend-icon="mdi-lan"
        class="text-caption"
        >
        <v-btn variant="text" text="Local de Instalação" to="/DM253/Banco/" class="text-caption font-weight-regular"></v-btn>
      </v-list-item>

        <v-list-item
        prepend-icon="mdi-home-group-plus"
        class="text-caption"
        >
        <v-btn variant="text" text="Cadastrar" to="/DM253/Banco/cadastrar"  class="text-caption font-weight-regular"></v-btn>
      </v-list-item>


      
    
    </div>

<!--PLANEJAMENTO-->

<div>



      <div class="d-flex  align-center pl-4 my-4"  >
          <div class="w-auto mr-4 font-weight-black " style="font-size: 12px;" >Planejamento</div>
          <div class="w-75" ><hr></div>
        </div>

        <v-list-item
          v-for="[icon, text, to] in links"
          :key="icon"
          :prepend-icon="icon"
          link
          class="text-caption"
          :href="to"
        >
        <v-btn variant="text" :text="text" :to="to" class="text-caption font-weight-regular"></v-btn>
      </v-list-item>
     
    </div>
    

    <!--Check-List-->
    <div>


      <div class="d-flex  align-center pl-4 mb-2 mt-4"  >
          <div class="w-auto mr-4 font-weight-black " style="font-size: 12px;" >Check-list de Inspeção</div>
          <div class="w-75" ><hr></div>
        </div>

        <v-list-item
          prepend-icon="mdi-database-settings"
          link
          class="text-caption"
          
        >
        <v-list-title><v-btn variant="text"  class="text-caption font-weight-regular">Carrregar</v-btn></v-list-title>
      </v-list-item>

      <v-list-item
          prepend-icon="mdi-list-status"
          link
          class="text-caption"
          
        >
        <v-list-title><v-btn variant="text"  class="text-caption font-weight-regular">Acompanhamento</v-btn></v-list-title>
      </v-list-item>
    </div>



    
    <!--Check-List-->
    <div>


<div class="d-flex  align-center pl-4 mb-2 mt-4"  >
    <div class="w-auto mr-4 font-weight-black " style="font-size: 12px;" > Inspeção</div>
    <div class="w-75" ><hr></div>
  </div>

  <v-list-item
    prepend-icon="mdi-database-settings"
    link
    class="text-caption"
    
  >
  <v-list-title><v-btn variant="text"  class="text-caption font-weight-regular">  Carga</v-btn></v-list-title>
</v-list-item>

<v-list-item
    prepend-icon="mdi-list-status"
    link
    class="text-caption"
    
  >
  <v-list-title><v-btn variant="text"  class="text-caption font-weight-regular">Acompanhamento</v-btn></v-list-title>
</v-list-item>
</div>








      </v-list>
      </v-navigation-drawer>
      
      <slot />

    </v-app>
   
</template>



<script setup>
import { ref } from 'vue'

const drawer = ref(false)





const links = [
  ['mdi-account-search', 'Cadastrar', '/DM253/Planejamento/cadastrar'],
  ['mdi-text-search-variant', 'Listar', '/DM253/Planejamento/cadastrar'],
]

const relatorio=  ['Sensitiva', 'Análise de Vibração']

const relatorio2=  ['Sensitiva', 'Análise de Vibração']



</script>



  