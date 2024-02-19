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
                    <td colspan="1" class="text-center ">{{ user.id}}</td>
                    <td colspan="6" class="text-center ">{{ user.username }}</td>
                    <td colspan="6" class="text-center "> {{ user.email }}</td>
                    <td colspan="3"> 
                        <div class="d-flex justify-end">

                           <update :IdUser="user.id" :Username="user.username " :Useremail="user.email"/>
                        
                           <delete :IdUser="user.id" :Username="user.username "/>
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
    const { data: users, pending,refresh } = await useFetch("https://localhost:7021/listarUsuarios", {
        method: "GET",
        headers:{
            "content-type": "application/json"
        },
        lazy:true,
        server:false,
      
       
    })
</script>