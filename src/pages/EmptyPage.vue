<script setup lang="ts">
import CardComponent from "src/components/CardComponent.vue";
import { useStore } from "src/stores/store";
import { ref } from "vue";
import { onMounted } from "vue";
import NewEditDialog from "src/components/NewEditDialog.vue";

const store = useStore();
const selectedCategoryName = ref(store.many.documents[0]);
const list = ref(store.other.documents);
onMounted(() => {
  store.getAllCategories();
  store.one_GetAll();
  store.other_GetAll(selectedCategoryName.value.nev);
  selectionChanged();
});
function selectionChanged() {
  if (selectedCategoryName.value === null) {
    return;
  }
  // store.other_GetAll(selectedCategoryName.value.nev);
  console.log(selectedCategoryName.value.nev);
}
function editDocument() {
  store.app.showEditDialog = true;
}

// console.log(store.one.documents[0]);
</script>
<template>
  <!-- <p v-for="(item, index) in store.one.documents" :key="index">{{ item }}</p> -->
  <q-page>
    <div class="row justify-center">
      <q-select
        v-model="selectedCategoryName"
        clearable
        emit-value
        label="Kategória"
        map-options
        option-label="nev"
        option-value="nev"
        :options="store.many.documents"
        :rules="[(v) => v != null || 'Kérem válasszon kategóriát!']"
        @update:model-value="selectionChanged()"
      ></q-select>
    </div>
    <div class="row justify-center q-ma-xl">
      <div v-for="(item, index) in list" :key="index" class="col-xs-12 col-sm-6 col-md-4 col-lg-3">
        <CardComponent :index="index" @editDialog="editDocument()"></CardComponent>
      </div>
    </div>
  </q-page>
  <NewEditDialog />
</template>
<style lang="scss" scoped></style>
