<template>
  <div class="mt-16">
    <v-container>
      <v-btn prepend-icon="mdi-arrow-left-circle" to="/DM253" variant="plain" color="red-darken-4">Voltar</v-btn>
        <h1 class="text-h3 mt-4 mb-10 font-weight-bold text-cyan-darken-4" style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;">Local da Instalação</h1>
        
      <v-form class="w-75 mx-auto h-100  bg-grey-lighten-3 pa-8 rounded-lg">
        <v-row>
          <v-col cols="12">       
            <v-text-field label="Responsavél" variant="solo-inverted" density="compact"></v-text-field>
          </v-col>
          <v-col cols="12">   
       
            <v-text-field label="Responsavél" variant="solo-inverted" density="compact"></v-text-field>
          </v-col>
          <v-col cols="12">   
                   
            <v-text-field label="Responsavél" variant="solo-inverted" density="compact"></v-text-field>
          </v-col>
        </v-row>


        <v-row>
          <v-col></v-col>
        </v-row>
      </v-form>
    </v-container>
  </div>
</template>

<script setup>
definePageMeta({
  layout: 'dms',
});

</script>