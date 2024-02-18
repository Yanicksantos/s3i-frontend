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
                <tbody >
                <tr
                    v-for="item in desserts"
                    :key="item.name"
                >
                    <td colspan="1" class="text-center ">{{ item.id}}</td>
                    <td colspan="6" class="text-center ">{{ item.calories }}</td>
                    <td colspan="6" class="text-center "> {{ item.caloriess }}</td>
                    <td colspan="3"> 
                        <div class="d-flex justify-end">

                           <update :IdUser="item.id" />
                        
                           <delete :IdUser="item.id"/>
                        </div>
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
import Delete from '~/components/Delete.vue'
import modal from '~/components/modal.vue'
import Update from '~/components/Update.vue'
  export default {
  components: { modal, Update, Delete },
    data () {
      return {
        desserts: [
          {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 1
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 2
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 3
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 4
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 5
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 6
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 7
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 8
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 9
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 10
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 11
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 12
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 13
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 14
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 15
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 16
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 17
          },
           {
            name: '1',
            calories: 'yanick Manuel Eduardo dos Santos',
             caloriess: 'yanickteste@teste.com',
             id: 18
          },
          
       
        ],
      }
    },
  }
</script>