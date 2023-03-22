<template>
  <div class="q-pa-md">
    <p style="text-align: center">Editar Módulo</p>
    <q-form @submit="onAtualizar" @reset="onReset">
      <!-- Input -->
      <div style="width: 600px; margin: 0 auto">
        <q-input
          v-model="form.nome"
          outlined
          label="Nome do Módulo*"
          stack-label
        />
        <q-input
          v-model="form.nota1"
          outlined
          label="Nota 1"
          stack-label
          style="margin-top: 15px"
        />
        <q-input
          v-model="form.nota2"
          outlined
          label="Nota 2"
          stack-label
          style="margin-top: 15px"
        />
        <q-input
          v-model="form.nota3"
          outlined
          label="Nota 3"
          stack-label
          style="margin-top: 15px"
        />
      </div>

      <div style="margin-top: 50px; text-align: center">
        <q-btn label="Atualizar" type="submit" color="primary" />
        <q-btn label="Cancelar" type="reset" color="primary" flat />
      </div>
    </q-form>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter, useRoute } from "vue-router";

const router = useRouter();
const route = useRoute();
const id = route.params.id;

const form = ref({
  nome: "",
  nota1: "",
  nota2: "",
  nota3: "",
  id_aluno: Number(id), // associa o módulo com o usuário
});

async function onAtualizar() {
  console.log("Atualizando os dados do módulo do Aluno");
  setTimeout(() => router.push(`/modulos/${id}`), 1500); // "/modulos/" + id
}

function onReset() {
  form.value.nome = "";
  form.value.nota1 = "";
  form.value.nota2 = "";
  form.value.nota3 = "";

  setTimeout(() => router.push(`/modulos/${id}`), 700);
}
</script>

<style scoped>
p {
  font-size: 2em;
}
</style>
