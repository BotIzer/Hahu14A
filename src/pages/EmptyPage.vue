<script setup lang="ts">
import CardComponent from "src/components/CardComponent.vue";
import { useStore } from "src/stores/store";
import { ref, watch } from "vue";
import { onMounted } from "vue";
import NewEditDialog from "src/components/NewEditDialog.vue";

const store = useStore();
const selectedCategoryName = ref("Személyautó");
const list = ref([]);
onMounted(() => {
  store.getAllCategories();
  store.one_GetAll();
  // store.other_GetAll(selectedCategoryName.value.nev);
  store.other_GetAll(selectedCategoryName.value);
  selectionChanged();
});
const selectionChanged = () => {
  store.other_GetAll(selectedCategoryName.value);
};
function editDocument(ad) {
  store.many.document._id = ad._id;
  store.app.showEditDialog = true;
}
watch(
  () => store.other.documents,
  (newDocuments) => {
    list.value = newDocuments;
  },
);
</script>
<template>
  <!-- <p v-for="(item, index) in store.one.documents" :key="index">{{ item }}</p> -->
  <q-page>
    <div class="row justify-center">
      <q-select
        v-model="selectedCategoryName"
        emit-value
        label="Kategória"
        map-options
        option-label="nev"
        option-value="nev"
        :options="store.many.documents"
        @update:model-value="selectionChanged()"
      ></q-select>
    </div>
    <div class="row justify-center q-ma-xl">
      <div v-for="(item, index) in list" :key="index" class="col-xs-12 col-sm-6 col-md-4 col-lg-3">
        <CardComponent :index="index" @editDialog="editDocument(item)"></CardComponent>
      </div>
    </div>
  </q-page>
  <NewEditDialog />
</template>
<style lang="scss" scoped></style>
