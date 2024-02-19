<script>
import { useStore } from "src/stores/store";
import { ref } from "vue";
const store = useStore();
export default {
  props: ["index"],
  setup(props) {
    const _id = ref(store.one.documents[props.index]._id);
    const cim = ref(store.one.documents[props.index].cim);
    const displayText = ref(store.one.documents[props.index].leiras);
    const szin = ref(store.one.documents[props.index].szin);
    const evjarat = ref(store.one.documents[props.index].evjarat);
    const hengerurtartalom = ref(store.one.documents[props.index].hengerurtartalom);
    const hirdetes_datum = ref(store.one.documents[props.index].hirdetes_datum);
    const kepek = ref(store.one.documents[props.index].kepek);
    // console.log(kepek.value);
    const slicedText = ref("");
    const toggled = ref(false);
    const handleToggle = (toggled) => {
      if (!toggled) {
        let lastWhiteSpaceIdx = -1;
        for (let index = 0; index < 100; index++) {
          slicedText.value += displayText.value[index];
          if (displayText.value[index] == " ") {
            lastWhiteSpaceIdx = index;
          }
        }
        if (slicedText.value[99] == " ") {
          slicedText.value = slicedText.value.slice(0, 98) + "...";
        } else {
          slicedText.value = slicedText.value.slice(0, lastWhiteSpaceIdx) + "...";
        }
      } else {
        slicedText.value = displayText.value;
      }
    };

    return {
      toggled,
      displayText,
      _id,
      cim,
      szin,
      evjarat,
      hengerurtartalom,
      hirdetes_datum,
      slicedText,
      kepek,
      handleToggle,
    };
  },
  mounted() {
    this.handleToggle(false);
  },
};
</script>

<template>
  <q-card bordered class="q-ma-md" flat>
    <q-card-section class="text-center text-h5" style="background-color: rgb(200, 190, 156)">
      {{ cim }}
    </q-card-section>
    <q-card-section class="text-h7" style="background-color: rgb(255, 228, 196)">
      <ul>
        <li>
          <span>Szin: </span><b>{{ szin }}</b>
        </li>
        <li>
          <span>Évjárat: </span><b>{{ evjarat }}</b>
        </li>
        <li>
          <span>Hengerűrtartalom: </span><b>{{ hengerurtartalom }} cm<sup>2</sup></b>
        </li>
        <li>
          <span>Hirdetés dátuma: </span><b>{{ hirdetes_datum }}</b>
        </li>
      </ul>
    </q-card-section>
    <q-card-section class="" style="background-color: rgb(200, 190, 156)">
      <div class="text-h7 text-justify">{{ toggled ? displayText : slicedText }}</div>
      <hr />
      <q-toggle
        v-model="toggled"
        color="dark-blue"
        :disable="displayText.length <= 100"
        label="Teljes hirdetés"
        @update:model-value="handleToggle"
      />
    </q-card-section>
    <q-card-section style="background-color: rgb(255, 228, 196)">
      <q-carousel v-model="_id" thumbnails>
        <q-carousel-slide v-for="(item, index) in kepek" :key="index" :img-src="kepek[index]" :name="index" />
      </q-carousel>
    </q-card-section>
    <q-card-section style="background-color: rgb(200, 190, 156)">
      <div v-for="item in kepek" :key="item" class="text-h7 text-justify">{{ item }}</div>
    </q-card-section>
    <q-card-actions class="justify-center" style="background-color: rgb(255, 228, 196)">
      <q-btn
        class="bg-green-3"
        label="Hirdetés szerkesztése"
        no-caps
        type="button"
        @click="$emit('editDialog')"
      ></q-btn>
    </q-card-actions>
  </q-card>
</template>
<style lang="sass" scoped></style>
