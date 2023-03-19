<template>
  <div class="q-pa-md">
    <q-table
      title="Módulo"
      :rows="rows"
      :columns="columns"
      row-key="id"
      :filter="filter"
      :loading="loading"
    >
      <template v-slot:top>
        <q-btn
          color="primary"
          :disable="loading"
          label="Adicionar Módulo"
          @click="addAluno"
        />
        <q-space />
        <q-input
          filled
          borderless
          dense
          debounce="300"
          color="primary"
          v-model="filter"
          label="Pesquisar"
        >
          <template v-slot:append>
            <q-icon name="search" />
          </template>
        </q-input>
      </template>

      <template v-slot:body-cell-acoes="props">
        <q-td :props="props">
          <q-btn
            size="sm"
            icon="edit"
            class="q-mx-sm q-px-sm"
            title="Editar Aluno"
            color="orange-8"
            @click="editAluno(props.row.id)"
          />
        </q-td>
      </template>
    </q-table>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { useQuasar } from "quasar";
import { useRouter } from "vue-router";
import { api } from "src/boot/axios";
import routes from "src/router/routes";

const columns = [
  {
    name: "nome",
    required: true,
    label: "Nome Completo",
    align: "left",
    field: "nome",
  },
  {
    name: "nota1",
    required: true,
    label: "Nota 1",
    align: "center",
    field: "nota1",
  },
  {
    name: "nota2",
    required: true,
    label: "Nota 2",
    align: "center",
    field: "nota2",
  },
  {
    name: "nota3",
    required: true,
    label: "Nota 3",
    align: "center",
    field: "nota3",
  },
  {
    name: "situacao",
    label: "Situação",
    align: "center",
    field: "situacao",
  },
  {
    name: "acoes",
    label: "Ações",
    align: "center",
    field: "acoes",
  },
];

const rows = ref([]);

async function buscaDados() {
  const { data } = await api.get("/modulo");
  console.log(data);
  rows.value = data;
}

const router = useRouter();
const $q = useQuasar();
const search = ref("");

function addAluno() {
  router.push("/cadastroModulo");
}

function editAluno() {
  console.log("Editando o Aluno...");
}

onMounted(() => {
  buscaDados();
});
</script>

<style scoped></style>
