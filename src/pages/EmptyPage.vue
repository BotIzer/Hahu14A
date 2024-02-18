<script setup lang="ts">
import CardComponent from "src/components/CardComponent.vue";
</script>

<template>
  <q-page>
    <div class="row justify-center">
      <q-select
        class="q-field--float col-xs-5 col-sm-4 col-md-3 col-lg-2 col-xl-1"
        label="Kategóriák"
        model-value=""
      ></q-select>
    </div>
    <div class="row justify-center q-ma-xl">
      <div class="col-sm-12 col-md-6 col-l-4 col-xl-3">
        <CardComponent></CardComponent>
      </div>
    </div>
  </q-page>
</template>

<style lang="scss" scoped></style>
