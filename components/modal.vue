<template>
  <div class="h-25">
    <h1>LISTA DE USUÁRIOS - S3I</h1>

    <v-dialog v-model="dialog" persistent width="400">
      <template v-slot:activator="{ props }">
        <v-btn
          v-bind="props"
          prepend-icon="mdi-plus"
          color="#4CAF50"
          class="mb-6 mt-4"
          size="large"
        >
          Adicionar
        </v-btn>
      </template>
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
                :items="['California', 'Colorado', 'Florida']"
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
      </v-card>
    </v-dialog>

    <hr>
  </div>
</template>

<script>
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
    onSubmit() {
      if (!this.form || !this.validateForm()) return;

      this.loading = true;

      setTimeout(() => {
        this.loading = false;
        this.dialog = false;

        alert(
          `Nome: ${this.nome}\nE-mail: ${this.email}\nCargo: ${this.cargo}\nAniversário: ${this.selectedDate}`
        );

        this.nome ='',
        this.email ='',
        this.selectedDate = '',
        this.cargo =''
      }, 2000);
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
        this.required(this.cargo) &&
        this.required(this.selectedDate)
      );
    },
  },
};
</script>
