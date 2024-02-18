<template>
    <div>
        <v-btn color="#B71C1C" icon="mdi-delete-forever" @click="teste1()" variant="text"></v-btn>
    

        <v-dialog v-model="dialog" persistent width="400">    
            <v-card>
                <v-card-item>
                    <v-card-title>
                        Excluir usuario
                    </v-card-title>
                    <v-card-text >
                       <p class="mt-4">Tem certeza que deseja excluir esse usuário?</p>
                    </v-card-text>
                

                    <v-card-actions>
                        <v-spacer></v-spacer>
                        <v-btn
                        variant="outlined"
                        @click="dialog = false"
                        color="blue-grey-darken-4"
                        class="mr-2"
                        
                        >
                        Cancelar
                        </v-btn>
                        <v-btn
                        @click="Submit()"
                        :loading="loading"
                        variant="flat"
                        color="#B71C1C"
                      
                        
                        >
                        Excluir
                        </v-btn>
                    </v-card-actions>
                </v-card-item>   
            </v-card>
        </v-dialog>
            
    </div>
</template>

<script>
export default {
 props: {
    IdUser: {
      type: Number, 
      required: true,
    },
  },
  data: () => ({
    dialog: false,
    loading: false,

  }),

  methods: {
    teste1() {
         this.nome =` teste de ${this.IdUser}` ;
        this.dialog = true;
       
       


    },

    Submit() {
      this.loading = true;

      setTimeout(() => {
        this.loading = false;
        this.dialog = false;
        
      }, 2000);
    },
    
 


   
  },
};
</script>
