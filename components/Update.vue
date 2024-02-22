<template>
    <div>
    <v-btn  color="#1A237E" icon="mdi-pencil" @click="teste()" variant="text"></v-btn>

    <v-dialog v-model="dialog" persistent width="400">    
      <v-card>
        <v-card-item>
          <v-card-title>
            <h4 class="text-h5 mb-8">Editar</h4>
          </v-card-title>
               <v-card-item v-if="pending">
                     <v-progress-linear indeterminate 
                       absolute
                     bottom
                     ></v-progress-linear>
                 </v-card-item>
          <v-card-text v-else>
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

                <!--<v-select
                v-model="cargo"
                label="Cargo"
                :items="['Administrador', 'Analista', 'Assistente', 'Auxiliar']"
                :readonly="loading"
                :rules="[required]"
                variant="outlined"
                density="compact"
              ></v-select>-->

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
        
    </div>
</template><script>
import { ref } from 'vue';
import { format } from 'date-fns';

export default {
  props: {
    Userbirthdate: {
      type: String,
      required: true,
    },
    Username: {
      type: String,
      required: true,
    },
    Useremail: {
      type: String,
      required: true,
    },
    IdUser: {
      type: Number,
      required: true,
    },
  },
  setup(props) {
    const dialog = ref(false);
    const form = ref(false);
    const email = ref(null);
    const password = ref(null);
    const loading = ref(false);
    const selectedDate = ref('');
    const nome = ref('');
    const cargo = ref('');
    const validEmail = ref(true);
    const id = ref(null);

    const formatarData = (data) => {
      return format(new Date(data), 'yyyy-MM-dd');
    };

    const teste = async () => {
      id.value = props.IdUser;
      email.value = props.Useremail;
      nome.value = props.Username;
      selectedDate.value = formatarData(props.Userbirthdate);
      dialog.value = true;
    };

    const onSubmit = async () => {
      if (!form.value || !validateForm()) return;

      loading.value = true;
      const userapi = {
        name: nome.value,
        email: email.value,
        birthdate: "2024-02-21T18:40:03.487Z"
      };

      await useFetch(`https://usuarioapi.up.railway.app/api/Users/Update?id=${id.value}`, {
        method: 'PUT',
        headers: {
          'content-type': 'application/json',
        },
        body: JSON.stringify(userapi),
        lazy: true,
        server: false,
      });

      loading.value = false;
      dialog.value = false;

      nome.value = '';
      email.value = '';
      selectedDate.value = '';
      cargo.value = '';

      alert("Usuário atualizado com sucesso!");
    };

    const required = (v) => !!v || '';

    const emailRule = (v) => {
      validEmail.value = /^\S+@\S+\.\S+$/.test(v);
      return validEmail.value || 'E-mail inválido.';
    };

    const validateForm = () => {
      return (
        required(nome.value) &&
        required(email.value) &&
        emailRule(email.value) &&
        required(selectedDate.value)
      );
    };

    return {
      dialog,
      form,
      email,
      password,
      loading,
      selectedDate,
      nome,
      cargo,
      validEmail,
      teste,
      onSubmit,
      required,
      emailRule,
      validateForm,
    };
  },
};
</script>
