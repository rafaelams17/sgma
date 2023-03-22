<template>
  <div class="q-pa-md">
    <p style="text-align: center">Editar Aluno</p>
    <q-form @submit="onAtualizar" @reset="onReset">
      <!-- Input dos dados do Aluno -->
      <div style="width: 600px; margin: 0 auto">
        <q-input
          type="text"
          v-model="form.nome"
          outlined
          label="Nome *"
          stack-label
          style="margin-bottom: 15px"
        />

        <q-input
          type="date"
          v-model="form.data_nasc"
          outlined
          label="Data de Nascimento *"
          stack-label
        />
        <q-input
          type="text"
          v-model="form.cpf"
          outlined
          label="CPF *"
          stack-label
          style="margin-top: 15px"
        />
      </div>

      <!-- Botões -->

      <div style="margin-top: 50px; text-align: center">
        <q-btn label="Atualizar" type="submit" color="primary" />
        <q-btn label="Cancelar" type="reset" color="primary" flat />
      </div>
    </q-form>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";

const router = useRouter(); //

const form = ref({
  nome: "",
  data_nasc: "",
  cpf: "",
});

function onAtualizar() {
  console.log("Atualizando os dados do Aluno!");
}

function onReset() {
  form.value.nome = "";
  form.value.data_nasc = "";
  form.value.cpf = "";

  setTimeout(() => router.push("/alunos"), 700);
}
</script>

<style scoped>
p {
  font-size: 2em;
}
</style>
