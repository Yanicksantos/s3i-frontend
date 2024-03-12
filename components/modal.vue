<template>
  <div class="">

    <v-dialog v-model="dialog" persistent width="900">
      <template v-slot:activator="{ props }">
        <v-btn
          v-bind="props"
          prepend-icon="mdi-plus"
          color="#4CAF50"
          class="px-4 ml-4 mt-6"
          variant="flat"
        >
          Novo Usuario
        </v-btn>
      </template>



      
      <v-card
        prepend-icon="mdi-account"
        title="Adicionar Usuário"
      >
        <v-card-text class="pt-10">
          <v-row dense>
            <v-col
              cols="12"
              md="4"
              sm="6"
              
            >
              <v-text-field
                label="Nome*"
                required
                variant="outlined"
                density="compact"
              ></v-text-field>
            </v-col>

            <v-col
              cols="12"
              md="3"
              sm="6"
            >
              <v-text-field
                label="Login*"
                variant="outlined"
                density="compact"
                required

              ></v-text-field>
            </v-col>

            <v-col
              cols="12"
              md="5"
              sm="6"
            >
            <v-text-field
                label="Email*"
                variant="outlined"
                density="compact"
                required
              ></v-text-field>
        
             
            </v-col>

            <v-col
              cols="12"
              md="2"
              sm="6"
            >
            <v-autocomplete
                :items="['P2', 'P3', 'P4', 'P5', 'P6']"
                label="Perfil*"
                variant="outlined"
                density="compact"
              ></v-autocomplete>
            </v-col>

            <v-col
              cols="12"
              md="4"
              sm="6"
            >
            <v-text-field
                label="Telefone"
                variant="outlined"
                density="compact"
              ></v-text-field>
            </v-col>

            <v-col
              cols="12"
              md="6"
              sm="6"
            >
            <v-autocomplete
                :items="['Equipe Geral', 'Equipe Instalação Elétrica', 'Equipe de Mnautenção Mecânica', 'Equipe de Teste']"
                label="Equipe"
                variant="outlined"
                density="compact"
                disabled
              ></v-autocomplete>
              
            </v-col>
 

            <v-col
              cols="12"
              sm="6"
            >
            <v-text-field
                label="Senha*"
                type="password"
                required
              ></v-text-field>
            </v-col>

            <v-col
              cols="12"
              sm="6"
            >
            <v-text-field
                label="Confirmar Senha*"
                type="password"
                required
                disabled
              ></v-text-field>
            </v-col>
            <v-col
              cols="12"
              md="3"
              sm="6"
            >
            <v-autocomplete
                :items="['Ativo', 'Desativado']"
                label="Status"
                variant="outlined"
                density="compact"
              ></v-autocomplete>
              
            </v-col>
          </v-row>

          <small class="text-caption text-medium-emphasis">* Indica campo Obrigatório</small>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>

          <v-btn
            text="Cancelar"
            variant="plain"
            @click="dialog = false"
          ></v-btn>

          <v-btn
            color="primary"
            text="Salvar"
            variant="tonal"
            @click="dialog = false"
          ></v-btn>
        </v-card-actions>
      </v-card>


      <!--
      <v-card>
        <v-card-item>
          <v-card-title>
            <h4 class="text-h5 mb-8">Adicionar Usuário</h4>
          </v-card-title>

          <v-card-text>
            <v-form v-model="form" @submit.prevent="onSubmit">
              <v-text-field
                v-model="nome"
                :readonly="loading"
                :rules="[required]"
                class="mb-2 mt-4"
                label="Nome*"
                variant="outlined"
                density="compact"
              ></v-text-field>

              <v-text-field
                v-model="email"
                :readonly="loading"
                :rules="[required, emailRule]"
                type="email"
                required
                class="mb-2"
                label="E-mail*"
                variant="outlined"
                density="compact"
              ></v-text-field>

              <v-select
                v-model="cargo"
                label="Cargo"
                :items="['Administrador', 'Analista', 'Assistente', 'Auxiliar']"
                :readonly="loading"
                :rules="[required]"
                variant="outlined"
                density="compact"
              ></v-select>

              <v-text-field
                v-model="selectedDate"
                label="Aniversário*"
                type="date"
                :readonly="loading"
                :rules="[required]"
                variant="outlined"
                density="compact"
                class="mb-4"
              ></v-text-field>

              <v-card-actions>
                <v-btn
                  variant="flat"
                  @click="dialog = false"
                  color="#B71C1C"
                >
                  Cancelar
                </v-btn>
                <v-btn
                  :disabled="!form || !validEmail"
                  :loading="loading"
                  size="large"
                  type="submit"
                  variant="flat"
                  color="blue-darken-1"
                >
                  Salvar
                </v-btn>
              </v-card-actions>
            </v-form>
          </v-card-text>
        </v-card-item>
      </v-card>-->
    </v-dialog>
  </div>
</template>

<script>
 import { format } from 'date-fns';
export default {
   data: () => ({
    dialog: false,
    form: false,
    email: null,
    password: null,
    loading: false,
    selectedDate: '',
    nome: '',
    cargo: '',
    validEmail: true,
  }),

  methods: {
 
   async onSubmit() {
      if (!this.form || !this.validateForm()) return;

      this.loading = true;

   
      var dataFormatada = this.selectedDate;

      // Dividir a string para obter os componentes de dia, mês e ano
      var partes = dataFormatada.split('-');
      var ano = partes[0];
      var mes = partes[1];
      var dia = partes[2];

      // Construir a string no formato "yyyy-mm-ddTHH:mm:ss.SSSZ"
      var dataConvertida = ano + '-' + mes + '-' + dia + 'T00:00:00.000Z';

    


    const userapi = {
      name: this.nome,
      email: this.email,
      birthdate: dataConvertida
    };
    
    const { data, pending } = await useFetch('https://usuarioapi.up.railway.app/api/Users/Insert', {
      method: 'POST',
      headers: {
        'content-type': 'application/json',
      },
      body: JSON.stringify(userapi),
      lazy: true,
      server: false,
    });

    this.nome ='',
    this.email ='',
    this.selectedDate = '',
  
    this.loading = false;
  
      this.dialog = false;
          alert("Usuario Adicionado com sucesso!");

      
    },

    
    required(v) {
      return !!v || '';
    },
    emailRule(v) {
      this.validEmail = /^\S+@\S+\.\S+$/.test(v);
      return this.validEmail || 'E-mail inválido.';
    },
    validateForm() {
      return (
        this.required(this.nome) &&
        this.required(this.email) &&
        this.emailRule(this.email) &&
        this.required(this.selectedDate)
      );
    },
  },
};
</script>
