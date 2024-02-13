<script>
import { ref } from "vue";

export default {
  setup() {
    return {
      value: ref(true),
    };
  },
};
</script>
<template>
  <div class="col-sm-12 col-md-6 col-l-4 col-xl-3">
    <q-card bordered flat>
      <q-card-section class="text-center text-h5" style="background-color: rgb(200, 190, 156)">
        Our Changing Planet
      </q-card-section>
      <q-card-section class="text-h7" style="background-color: rgb(255, 228, 196)">
        <ul>
          <li>Szin:</li>
          <li>Évjárat:</li>
          <li>Hengerűrtartalom:</li>
          <li>Hirdetés dátuma:</li>
        </ul>
      </q-card-section>
      <q-card-section class="" style="background-color: rgb(200, 190, 156)">
        <div class="text-h7 text-justify">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore
          magna aliqua.
        </div>
        <hr />
        <q-toggle v-model="template" label="Teljes hirdetés" />
      </q-card-section>
      <q-card-section> </q-card-section>
    </q-card>
  </div>
</template>

<style lang="sass" scoped></style>
