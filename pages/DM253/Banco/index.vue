<template>
    <div class="pt-16">
        <v-container>
          <v-btn prepend-icon="mdi-arrow-left-circle" to="/DM253" variant="plain" color="red-darken-4">Voltar</v-btn>
            <v-form class="w-50 my-4 mx-auto d-flex">
                <v-file-input
                accept="application/vnd.ms-excel, application/vnd.openxmlformats-officedocument.spreadsheetml.sheet"
                label="Importe um arquivo excel"
                prepend-icon="mdi-microsoft-excel"
                variant="outlined"
                clearable
                chips
                hide-details
                single-line
                density="compact"            
                ></v-file-input>
                <V-btn 
                variant="text" 
                prepend-icon="mdi-export-variant" 
                class="text-caption"
                color="teal-darken-4"
                >Converter arquivo</V-btn>
            </v-form>


            <v-card flat>
                <v-card-item>
                    <v-row>
                    <v-col cols="4">
                        <v-card-title>
                            <v-icon icon="mdi-lan" class="mr-4" color="teal-darken-4"></v-icon>
                            <v-text class="font-weight-black text-teal-darken-4">Local de Instalação</v-text>
                            <v-tooltip text="Atualizar">
                            <template v-slot:activator="{ props }">
                                <v-btn 
                               size="small"  color="#1A237E" variant="text"   icon="mdi-refresh" class="ml-4"
                                v-bind="props"
                                ></v-btn>
                            </template>
                        </v-tooltip>
                        </v-card-title>
                    </v-col>
                    <v-spacer></v-spacer>
                    <v-col cols="6">
                        <v-text-field
                        v-model="search"
                        label="Filtar"
                        prepend-inner-icon="mdi-magnify"
                        variant="outlined"
                        hide-details
                        single-line
                        density="compact"
                        ></v-text-field>
                    </v-col>
                </v-row> 

                </v-card-item>
                  

                <v-data-table-virtual
                :headers="headers"
                :items="desserts"
                :search="search"
                height="300"
                hover
                fixed-header
                density="compact"
                class="text-caption"
                >
                <template v-slot:item.codigo="{ item }" >
                    <v-text class="font-weight-black">{{item.codigo}}</v-text>
                </template>
                <template v-slot:item.tipoinstal="{ item }" >
                    <v-chip  :text=item.tipoinstal  variant="tonal" :color="item.tipoinstal === 'Elétrico'? 'green-darken-4':'indigo-darken-4'"  size="small" ></v-chip>
                </template>

                <template v-slot:item.actions="{ item }" >
                    <v-btn  color="#1A237E" icon="mdi-pencil"  variant="text"  size="small"></v-btn>
                </template>

                </v-data-table-virtual>

                <v-card-item>
                    <v-btn
                    prepend-icon="mdi-plus"
                    color="teal-darken-4" 
                    variant="flat"
                    class=" text-caption"
                    >Cadastrar Local de Instalação</v-btn>
                </v-card-item>
            </v-card>
        
        </v-container>

    </div>
</template>

<script setup>
import { ref, computed } from 'vue';

definePageMeta({
  layout: 'dms',
});



const search = ref('');

const headers = [
  {
    align: 'start',
    key: 'codigo',
    title: 'Código do Local',
  },
  { key: 'descricao', title: 'Descrição do Local' },
  { key: 'classificacao', title: 'Classificação', align: 'center' },
  //{ key: 'details', title: 'Detalhes da Instalação' },
  { key: 'tipoinstal', title: 'Tipo de Local', align: 'center' },
  { key: 'tipoInsp', title: 'Tipo de Inspeção', align: 'center' },
  { key: 'actions', title: '' },
];
const desserts = [
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS01',
    descricao: 'Sistema de ventilação de ar quente do torrador 01 (lado Triscafé)',
    classificacao: 'A',
    details: '',
    tipoinstal: 'Elétrico',
    tipoInsp: 'Termografia',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS02',
    descricao: 'Sistema de ventilação de ar quente do torrador 02 (lado Triscafé)',
    classificacao: 'B',
    details: '',
    tipoinstal: 'Mecânico',
    tipoInsp: 'Análise de Vibração',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS03',
    descricao: 'Sistema de ventilação de ar quente do torrador 03 (lado Triscafé)',
    classificacao: 'C',
    details: '',
    tipoinstal: 'Elétrico',
    tipoInsp: 'Sensitiva',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS04',
    descricao: 'Sistema de ventilação de ar quente do torrador 04 (lado Triscafé)',
    classificacao: 'A',
    details: '',
    tipoinstal: 'Mecânico',
    tipoInsp: 'Todas',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS05',
    descricao: 'Sistema de ventilação de ar quente do torrador 05 (lado Triscafé)',
    classificacao: 'B',
    details: '',
    tipoinstal: 'Elétrico',
    tipoInsp: 'Ultrassom',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS06',
    descricao: 'Sistema de ventilação de ar quente do torrador 06 (lado Triscafé)',
    classificacao: 'C',
    details: '',
    tipoinstal: 'Mecânico',
    tipoInsp: 'Sensitiva',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS07',
    descricao: 'Sistema de ventilação de ar quente do torrador 07 (lado Triscafé)',
    classificacao: 'A',
    details: '',
    tipoinstal: 'Elétrico',
    tipoInsp: 'Termografia',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS08',
    descricao: 'Sistema de ventilação de ar quente do torrador 08 (lado Triscafé)',
    classificacao: 'B',
    details: '',
    tipoinstal: 'Mecânico',
    tipoInsp: 'Análise de Vibração',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS09',
    descricao: 'Sistema de ventilação de ar quente do torrador 09 (lado Triscafé)',
    classificacao: 'C',
    details: '',
    tipoinstal: 'Elétrico',
    tipoInsp: 'Sensitiva',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS10',
    descricao: 'Sistema de ventilação de ar quente do torrador 10 (lado Triscafé)',
    classificacao: 'A',
    details: '',
    tipoinstal: 'Mecânico',
    tipoInsp: 'Todas',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS11',
    descricao: 'Sistema de ventilação de ar quente do torrador 11 (lado Triscafé)',
    classificacao: 'B',
    details: '',
    tipoinstal: 'Elétrico',
    tipoInsp: 'Ultrassom',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS12',
    descricao: 'Sistema de ventilação de ar quente do torrador 12 (lado Triscafé)',
    classificacao: 'C',
    details: '',
    tipoinstal: 'Mecânico',
    tipoInsp: 'Sensitiva',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS13',
    descricao: 'Sistema de ventilação de ar quente do torrador 13 (lado Triscafé)',
    classificacao: 'A',
    details: '',
    tipoinstal: 'Elétrico',
    tipoInsp: 'Termografia',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS14',
    descricao: 'Sistema de ventilação de ar quente do torrador 14 (lado Triscafé)',
    classificacao: 'B',
    details: '',
    tipoinstal: 'Mecânico',
    tipoInsp: 'Análise de Vibração',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS15',
    descricao: 'Sistema de ventilação de ar quente do torrador 15 (lado Triscafé)',
    classificacao: 'C',
    details: '',
    tipoinstal: 'Elétrico',
    tipoInsp: 'Sensitiva',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS16',
    descricao: 'Sistema de ventilação de ar quente do torrador 16 (lado Triscafé)',
    classificacao: 'A',
    details: '',
    tipoinstal: 'Mecânico',
    tipoInsp: 'Todas',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS17',
    descricao: 'Sistema de ventilação de ar quente do torrador 17 (lado Triscafé)',
    classificacao: 'B',
    details: '',
    tipoinstal: 'Elétrico',
    tipoInsp: 'Ultrassom',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS18',
    descricao: 'Sistema de ventilação de ar quente do torrador 18 (lado Triscafé)',
    classificacao: 'C',
    details: '',
    tipoinstal: 'Mecânico',
    tipoInsp: 'Sensitiva',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS19',
    descricao: 'Sistema de ventilação de ar quente do torrador 19 (lado Triscafé)',
    classificacao: 'A',
    details: '',
    tipoinstal: 'Elétrico',
    tipoInsp: 'Termografia',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS20',
    descricao: 'Sistema de ventilação de ar quente do torrador 20 (lado Triscafé)',
    classificacao: 'B',
    details: '',
    tipoinstal: 'Mecânico',
    tipoInsp: 'Análise de Vibração',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS21',
    descricao: 'Sistema de ventilação de ar quente do torrador 21 (lado Triscafé)',
    classificacao: 'C',
    details: '',
    tipoinstal: 'Elétrico',
    tipoInsp: 'Sensitiva',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS22',
    descricao: 'Sistema de ventilação de ar quente do torrador 22 (lado Triscafé)',
    classificacao: 'A',
    details: '',
    tipoinstal: 'Mecânico',
    tipoInsp: 'Todas',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS23',
    descricao: 'Sistema de ventilação de ar quente do torrador 23 (lado Triscafé)',
    classificacao: 'B',
    details: '',
    tipoinstal: 'Elétrico',
    tipoInsp: 'Ultrassom',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS24',
    descricao: 'Sistema de ventilação de ar quente do torrador 24 (lado Triscafé)',
    classificacao: 'C',
    details: '',
    tipoinstal: 'Mecânico',
    tipoInsp: 'Sensitiva',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS25',
    descricao: 'Sistema de ventilação de ar quente do torrador 25 (lado Triscafé)',
    classificacao: 'A',
    details: '',
    tipoinstal: 'Elétrico',
    tipoInsp: 'Termografia',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS26',
    descricao: 'Sistema de ventilação de ar quente do torrador 26 (lado Triscafé)',
    classificacao: 'B',
    details: '',
    tipoinstal: 'Mecânico',
    tipoInsp: 'Análise de Vibração',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS27',
    descricao: 'Sistema de ventilação de ar quente do torrador 27 (lado Triscafé)',
    classificacao: 'C',
    details: '',
    tipoinstal: 'Elétrico',
    tipoInsp: 'Sensitiva',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS28',
    descricao: 'Sistema de ventilação de ar quente do torrador 28 (lado Triscafé)',
    classificacao: 'A',
    details: '',
    tipoinstal: 'Mecânico',
    tipoInsp: 'Todas',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS29',
    descricao: 'Sistema de ventilação de ar quente do torrador 29 (lado Triscafé)',
    classificacao: 'B',
    details: '',
    tipoinstal: 'Elétrico',
    tipoInsp: 'Ultrassom',
  },
  {
    codigo: 'BIA01-SOL-TOR-TOR02-VEN01-POS30',
    descricao: 'Sistema de ventilação de ar quente do torrador 30 (lado Triscafé)',
    classificacao: 'C',
    details: '',
    tipoinstal: 'Mecânico',
    tipoInsp: 'Sensitiva',
  }
];

const filteredDesserts = computed(() => {
  return desserts.filter(dessert =>
    dessert.name.toLowerCase().includes(search.value.toLowerCase())
  );
});
</script>