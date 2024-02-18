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
          <li><span>Szin: </span><b>template</b></li>
          <li><span>Évjárat: </span><b>template</b></li>
          <li><span>Hengerűrtartalom: </span><b>template</b></li>
          <li><span>Hirdetés dátuma: </span><b>template</b></li>
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
      <q-card-section style="background-color: rgb(255, 228, 196)">
        <q-img role="img" src="../assets/logo.png" style="max-height: 200px"></q-img>
      </q-card-section>
      <q-card-section style="background-color: rgb(200, 190, 156)">
        <div class="text-h7 text-justify">link</div>
      </q-card-section>
      <q-card-actions class="justify-center" style="background-color: rgb(255, 228, 196)">
        <q-btn class="bg-green-3" label="Hirdetés szerkesztése" no-caps type="button"> </q-btn>
      </q-card-actions>
    </q-card>
  </div>
</template>

<style lang="sass" scoped></style>
