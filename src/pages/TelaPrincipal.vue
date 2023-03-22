<template>
  <q-page>
    <!-- <q-toolbar-title>Teste Dashboard</q-toolbar-title> -->
    <div class="dados" style="margin-left: 250px">
      <q-card class="my-card bg-purple text-white">
        <q-card-section>
          <div class="text-h6">
            <q-icon size="md" name="person" />
            <span> Alunos cadastrados</span>
          </div>
          <div class="text-h6">
            <p>Quantidade de aluno cadastrado</p>
          </div>
        </q-card-section>
      </q-card>
    </div>

    <div class="dados">
      <q-card class="my-card bg-amber text-white">
        <q-card-section>
          <div class="text-h6">
            <q-icon size="md" name="folder" />
            <span> Módulos cadastrados</span>
          </div>
          <div class="text-h6">
            <p>Quantidade de módulo cadastrado</p>
          </div>
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script setup></script>

<style scoped>
.dados {
  margin: 20px;
  margin-top: 50px;
  width: 500px;
  display: inline-block;
}
</style>
