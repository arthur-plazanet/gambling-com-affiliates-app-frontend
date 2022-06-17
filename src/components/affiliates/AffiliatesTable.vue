<template>
  <table>
    <tr>
      <th v-for="header in headers" :key="header">{{ header }}</th>
    </tr>
    <AffiliatesTableTr
      v-for="affiliate in affiliates"
      :key="affiliate.id"
      :affiliate="affiliate"
    ></AffiliatesTableTr>
  </table>
</template>

<script setup>
import { reactive } from "vue";
import AffiliatesTableTr from "./AffiliatesTableTr.vue";

defineProps({
  affiliates: Array,
});

const headers = reactive(["id", "name"]);
</script>
