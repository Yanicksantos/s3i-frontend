<template>
<div class="container">
   
    <v-container>
        <div class="pX-10  mx-auto">
         <div class="h-25">
            <h1 >LISTA DE USUÁRIOS - S3I </h1>
            <v-btn class="my-6" prepend-icon="mdi-plus" color="#4CAF50">Adicionar</v-btn>
         </div>
          <hr>
        <div class="mx-auto my-2">
           
            <v-card elevation="12 " class="my-4 px-2 py-6">
                <v-card-item>

              

           
            <v-table
                fixed-header
                height="350px"
             
            >
                <thead >
                <tr >
                    <th class="text-center font-weight-black" colspan="1">
                    #
                    </th>
                    <th class="text-center font-weight-black" colspan="6">
                    nome
                    </th>
                    <th class="text-center font-weight-black" colspan="6">
                    email
                    </th>
                    <th class="text-left" colspan="3">
                    
                    </th>
                </tr>
                </thead>
                <tbody >
                <tr
                    v-for="item in desserts"
                    :key="item.name"
                >
                    <td colspan="1" class="text-center ">{{ item.name }}</td>
                    <td colspan="6" class="text-center ">{{ item.calories }}</td>
                    <td colspan="6" class="text-center "> {{ item.caloriess }}</td>
                    <td colspan="3" class="text-right"> 
                        <v-btn class="mr-4" color="#1A237E">Editar</v-btn>
                        <v-btn color="#B71C1C">Deletar</v-btn>
                    </td>
                </tr>
                </tbody>
            </v-table>
              </v-card-item>
             </v-card>
        </div>
        </div>
   </v-container>
</div>
</template>

<script>
  export default {
    data () {
      return {
        desserts: [
          {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
          },
          
       
        ],
      }
    },
  }
</script>