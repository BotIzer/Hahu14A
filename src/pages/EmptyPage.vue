<script setup lang="ts">
import CardComponent from "src/components/CardComponent.vue";
import { useStore } from "src/stores/store";
import { onMounted } from "vue";
const store = useStore();
onMounted(() => {
  store.getAllCategories();
});
// export default {
//   data() {
//     return {
//       store,
//     };
//   },
//   computed: {
//     truncatedText() {
//       if (this.longText.length > 130) {
//         return this.longText.slice(0, 124) + "...";
//       } else {
//         return this.longText;
//       }
//     },
//   },
// };
</script>
<template>
  <p v-for="(item, index) in store.many.documents" :key="index">{{ item }}</p>
  <q-page>
    <div class="row justify-center"></div>
    <div class="row justify-center q-ma-xl">
      <div class="col-sm-12 col-md-6 col-l-4 col-xl-3">
        <CardComponent></CardComponent>
      </div>
    </div>
  </q-page>
</template>

<style lang="scss" scoped></style>
