<template>
  <div class="q-pa-md">
    <p style="text-align: center">Cadastro de Módulos</p>
    <q-form @submit="onSubmit" @reset="onReset">
      <!-- Input -->
      <div style="width: 600px; margin: 0 auto">
        <q-input
          v-model="form.nome"
          outlined
          label="Nome *"
          stack-label
          :dense="dense"
          :rules="nomeRules"
        />
        <q-input
          v-model="form.nota1"
          outlined
          label="Nota 1"
          stack-label
          :dense="dense"
        />
        <q-input
          v-model="form.nota2"
          outlined
          label="Nota 2"
          stack-label
          :dense="dense"
          style="margin-top: 15px"
        />
        <q-input
          v-model="form.nota3"
          outlined
          label="Nota 3"
          stack-label
          :dense="dense"
          style="margin-top: 15px"
        />
      </div>

      <div style="margin-top: 50px; text-align: center">
        <q-btn label="Cadastrar" type="submit" color="primary" />
        <q-btn
          label="Cancelar"
          type="reset"
          color="primary"
          flat
          class="q-ml-sm"
        />
      </div>
    </q-form>
  </div>
</template>

<script setup>
import { useQuasar } from "quasar";
import { useRouter } from "vue-router";
import { api } from "src/boot/axios";
import { ref } from "vue";

const $q = useQuasar();
const router = useRouter();

const form = ref({
  nome: "",
  nota1: "",
  nota2: "",
  nota3: "",
});

const nomeRules = [(nome) => (nome && nome.length > 0) || "Campo obrigatório"];

async function onSubmit() {
  const aluno = await api.post("/modulo", form.value);

  $q.notify({
    type: "info",
    message: "Módulo cadastrado com sucesso!",
    timeout: 1000,
  });

  setTimeout(() => router.push("/modulos"), 1500);
}

function onReset() {
  form.value.nome = "";
  form.value.nota1 = "";
  form.value.nota2 = "";
  form.value.nota3 = "";

  setTimeout(() => router.push("/modulos"), 700);
}
</script>

<style scoped>
p {
  font-size: 2em;
}
</style>
