<script>
import { ref } from "vue";

export default {
  setup() {
    const longText = ref(
      "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labores et dolore magna aliqua. Lorem ipsum dolor sit amet consectetur adipisicin elit. Animi assumenda amet temporibus ab! Velit quibusdam voluptate maxime commodi quis minima dolorum consectetur perferendis fuga atque cumque voluptatibus a, obcaecati odit. Lorem ipsum dolor, sit amet consectetur adipisicing elit. Nam consectetur repellendus quam odio impedit ad placeat distinctio consequuntur doloribus adipisci. Dolorem harum asperiores sed delectu recusandae nesciunt sunt nemo debitis.",
    );
    const toggled = ref(false);
    const handleToggle = (toggled) => {
      if (toggled) {
        let slicedText = "";
        let lastWhiteSpaceIdx = -1;
        for (let index = 0; index < 100; index++) {
          slicedText += longText.value[index];
          if (longText.value[index] == " ") {
            lastWhiteSpaceIdx = index;
          }
        }
        if (slicedText[99] == " ") {
          longText.value = slicedText.slice(0, 98);
        } else {
          longText.value = slicedText.slice(0, lastWhiteSpaceIdx);
        }
      } else {
        console.log("Is not toggled.");
      }
    };

    return {
      longText,
      toggled,
      handleToggle,
    };
  },
};
</script>

<template>
  <q-card bordered flat>
    <q-card-section class="text-center text-h5" style="background-color: rgb(200, 190, 156)">
      Our Changing Planet
    </q-card-section>
    <q-card-section class="" style="background-color: rgb(200, 190, 156)">
      <div class="text-h7 text-justify">{{ longText }}</div>
      <hr />
      <q-toggle
        v-model="toggled"
        color="dark-blue"
        :disable="longText.length <= 100"
        label="Teljes hirdetés"
        @update:model-value="handleToggle"
      />
    </q-card-section>
    <q-card-actions class="justify-center" style="background-color: rgb(255, 228, 196)">
      <q-btn class="bg-green-3" label="Hirdetés szerkesztése" no-caps type="button"></q-btn>
    </q-card-actions>
  </q-card>
</template>
