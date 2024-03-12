<template>

  <div class="h-screen d-flex flex-column" >
    <div class=" bg-grey-lighten-5" style="height: 50px;"></div>
    <div style="background-image: url('/apresentacao.jpeg'); background-size: cover;" class="h-100 d-flex justify-end align-center elevation-16">
      <div class=" w-100 h-100  d-flex justify-end">
        <div class="w-50 h-100 bg-purple-lighten-5 px-8 py-4 elevation-16" >
          <h1 class="text-h1 text-teal-darken-4  font-weight-black ">Seu marketplace de inspeções.</h1>
          <P class="text-h6 font-weight-thin my-8" style="font-family:Verdana, Geneva, Tahoma, sans-serif">Ajudamos indústrias a cuidar de seus ativos de forma eficiente.</P>
          <v-btn prepend-icon="mdi-arrow-right-bold-box" color="indigo-darken-4" size="x-large" to="/usuarios">Acessar</v-btn>
        </div>
      </div>
     
    </div>
    <div class="bg-grey-lighten-5" style="height: 50px;"></div>
   
  </div>
</template>

<script setup>
definePageMeta({
  layout: false,
});
</script>