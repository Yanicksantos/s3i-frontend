<template>
  <div class="">

    <v-dialog v-model="dialog" persistent width="900">
      <template v-slot:activator="{ props }">
        <v-btn
          v-bind="props"
          prepend-icon="mdi-plus"
          class="px-4 ml-4 mt-6"
          color="teal-darken-4" 
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
                v-model="nome"
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
                v-model="login"
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
                v-model="email"
                label="Email*"
                variant="outlined"
                density="compact"
                required
                :rules="[emailRule]"
              ></v-text-field>
            </v-col>

            <v-col
              cols="12"
              md="4"
              sm="6"
            >
              <v-text-field
                v-model="telefone"
                label="Telefone"
                variant="outlined"
                density="compact"
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
                v-model="perfil"
                required
              ></v-autocomplete>
            </v-col>

            <v-col
              cols="12"
              md="6"
              sm="6"
            >
              <v-autocomplete
                :items="['Equipe Geral', 'Equipe Instalação Elétrica', 'Equipe de Manutenção Mecânica', 'Equipe de Teste']"
                label="Equipe"
                variant="outlined"
                density="compact"
                :disabled="perfil == 'P2'"
              ></v-autocomplete>
            </v-col>

            <v-col
              cols="12"
              sm="6"
            >
              <v-text-field
                v-model="senha"
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
                v-model="ConfirmarSenha"
                label="Confirmar Senha*"
                type="password"
                required
                :disabled="senha.length < 4"
                :rules="[ConfirmarSenhaRule]"
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
                required
                v-model="status"
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
            :disabled="!validateForm()"
            @click="onSubmit"
          ></v-btn>
        </v-card-actions>
      </v-card>

    </v-dialog>

    <v-dialog
      v-model="dialog2"
      width="auto"
    >
    
      <v-card
        width="400"
        prepend-icon="mdi-check-circle"
        title="Atualização de Usuário"
        text="Usuario adicionado com sucesso"
        color="green-darken-3"
      >
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            text="Ok"
            @click="dialog2 = false"
            variant="text"
            size="small"
          ></v-btn>
        </v-card-actions>
         
 
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
  data: () => ({
    dialog: false,
    email: '',
    senha: '',
    ConfirmarSenha: '',
    nome: '',
    login: '',
    telefone: '',
    perfil: 'P2',
    dialog2: true,
    status: ''
  }),

  methods: {
    onSubmit() {
   
      this.dialog2 = true;
    },

    emailRule(value) {
      return /^\S+@\S+\.\S+$/.test(value) || 'Endereço de e-mail inválido.';
    },

    ConfirmarSenhaRule(value) {
      if (value !== this.senha) {
        return 'A senha confirmada não corresponde à senha principal.';
      }
      return true;
    },

    validateForm() {
      return (
        this.emailRule(this.email) &&
        this.nome.trim() !== '' &&
        this.login.trim() !== '' &&
        this.senha.length >= 4 &&
        this.ConfirmarSenha !== '' &&
        this.perfil !== '' &&
        this.status !== '' &&
        this.ConfirmarSenhaRule(this.ConfirmarSenha)
      );
    },
  }
}
</script>