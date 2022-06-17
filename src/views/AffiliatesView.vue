<template>
  <div class="affiliates">
    <input type="text" v-model="search" placeholder="Type something..." />
    <AffiliatesTable :affiliates="state.filteredAffiliates"></AffiliatesTable>
  </div>
</template>

<script setup>
import { ref, reactive, onMounted, watch } from "vue";
import axios from "axios";
import AffiliatesTable from "../components/affiliates/AffiliatesTable.vue";

const search = ref("");
const state = reactive({ affiliates: [], filteredAffiliates: [] });

onMounted(() => {
  axios.get("http://localhost/api/affiliates").then((response) => {
    state.affiliates = response.data;
    state.filteredAffiliates = response.data;
  });
});

watch(search, async (newSearch) => {
  state.filteredAffiliates = state.affiliates.filter((affiliate) =>
    affiliate.name.toLowerCase().includes(newSearch)
  );
});
</script>
<style scoped>
input {
  margin-bottom: 20px;
}
table {
  margin: auto;
}
</style>
