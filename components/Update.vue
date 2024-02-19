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
        
    </div>
</template>
<script>
import { ref } from 'vue';

export default {
  props: {
    IdUser: {
      type: Number,
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

    const teste = async () => {
        email.value =  props.Useremail;
        nome.value = props.Username;
        cargo.value = 'California';
        selectedDate.value = '18/02/2024';
        dialog.value = true;


        /*
        dialog.value = true;
      // Assuming `useFetch` is a function or composition API related to fetching data
      const requi = await useAsyncData('users', () => $fetch(`https://localhost:7021/usuario/${props.IdUser}`))

      /*const { data: users, pending, refresh } = await useFetch(`https://localhost:7021/usuario/${props.IdUser}`, {
        method: 'GET',
        headers: {
          'content-type': 'application/json',
        },
        lazy: true,
        server: false,
      });

      const { payload } = useNuxtApp();


    if(!payload.pending){
     
        nome.value = payload.data["users"].username;
        email.value = payload.data["users"].email;
        cargo.value = 'California';
        selectedDate.value = Date.now();
    }*/

      
    };

    const onSubmit = () => {
      if (!form.value || !validateForm()) return;

      loading.value = true;

      setTimeout(() => {
        loading.value = false;
        dialog.value = false;

        alert(
          `Nome: ${nome.value}\nE-mail: ${email.value}\nCargo: ${cargo.value}\nAniversário: ${selectedDate.value}`
        );

        nome.value = '';
        email.value = '';
        selectedDate.value = '';
        cargo.value = '';
      }, 2000);
    };

    const required = (v) => !!v || '';

    const emailRule = (v) => {
      validEmail.value = /^\S+@\S+\.\S+$/.test(v);
      return validEmail.value || 'E-mail inválido.';
    };

    const validateForm = () => {
      return required(nome.value) && required(email.value) && emailRule(email.value) && required(cargo.value) && required(selectedDate.value);
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
