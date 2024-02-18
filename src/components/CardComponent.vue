<script>
import { text } from "node:stream/consumers";
import { ref } from "vue";

export default {
  setup() {
    return {
      longText: ref(
        "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Lorem ipsum dolor sit amet consectetur adipisicin elit. Animi assumenda amet temporibus ab! Velit quibusdam voluptate maxime commodi quis minima dolorum consectetur perferendis fuga atque cumque voluptatibus a, obcaecati odit. Lorem ipsum dolor, sit amet consectetur adipisicing elit. Nam consectetur repellendus quam odio impedit ad placeat distinctio consequuntur doloribus adipisci. Dolorem harum asperiores sed delectu recusandae nesciunt sunt nemo debitis.",
      ),
      toggled: ref(false),
      handleToggle(toggled, longText) {
        if (toggled) {
          const wordArray = longText.split(" ");
          const letterCount = Math.sum(...wordArray.length);
          let textResult = longText;
          if (letterCount >= 100) {
            wordArray.splice(-1);
            return (textResult = wordArray.join(" "));
          }
          return textResult;
          console.log("Is toggled.");
        } else {
          console.log("Is not toggled.");
        }
      },
    };
  },
};
</script>
<template>
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
        {{ longText }}
      </div>
      <hr />
      <q-toggle
        v-model="toggled"
        color="dark-blue"
        :disable="longText.length <= 100"
        label="Teljes hirdetés"
        @update:model-value="handleToggle(toggled, longText)"
      />
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
</template>
<style lang="sass" scoped></style>
