<template>
<div class="container">
    <v-container>
        <div class="pX-10  mx-auto">
         <modal />
        <div class="mx-auto my-2">
           
            <v-card elevation="4" class="my-2 px-2 py-2 rounded-lg" >
                <v-card-item>

              

           
            <v-table
                fixed-header
                height="350"
             
            >
                <thead >
                <tr >
                    <th class="text-center font-weight-black" colspan="1">
                    Id
                    </th>
                    <th class="text-center font-weight-black" colspan="4">
                    nome
                    </th>
                    <th class="text-center font-weight-black" colspan="4">
                    email
                    </th>
                    <th class="text-center font-weight-black" colspan="4">
                    Aniversário
                    </th>
                    <th class="text-left" colspan="3">
                    
                    </th>
                </tr>
                </thead>
               
                  
                 <v-card-item v-if="pending">
                     <v-progress-linear indeterminate 
                       absolute
                     bottom
                     ></v-progress-linear>
                 </v-card-item>
                     

                <tbody v-else>
                <tr
                  
                    v-for="user in users"
                    :key="user.id"
                >
                    <td colspan="1" class="text-center ">{{ user.id }}</td>
                    <td colspan="4" class="text-center ">{{ user.name }} </td>
                    <td colspan="4" class="text-center ">{{ user.email }}</td>
                    <td colspan="4" class="text-center "> {{ formatarData(user.birthdate) }}</td>
                    <td colspan="3"> 
                        <div class="d-flex justify-end">

                           <update :IdUser="user.id" :Username="user.name" :Useremail="user.email" :Userbirthdate="user.birthdate"/>
                        
                           <delete :Username="user.name" :IdUser="user.id"/>
                        </div>
                    </td>
                </tr>
                </tbody>
            </v-table>
              </v-card-item>
              
             </v-card>
             <v-btn @click="refresh" class="m-2"  color="#1A237E">Atualizar</v-btn>
        </div>
        </div>
   </v-container>
</div>
</template>

<script setup>
import { format } from 'date-fns';

const { data: users, pending, refresh } = await useFetch("https://usuarioapi.up.railway.app/api/Users/GetUsers", {
    method: "GET",
    headers: {
        "content-type": "application/json"
    },
    lazy: true,
    server: false,
});

// Função para formatar a data
const formatarData = (data) => {
    return format(new Date(data), 'dd-MM-yyyy');
};

</script>
