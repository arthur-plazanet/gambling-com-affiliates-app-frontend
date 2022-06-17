<template>
  <tr>
    <td>{{ affiliate.id }}</td>
    <td>{{ affiliate.name }}</td>
  </tr>
</template>

<script setup>
defineProps({
  affiliate: Object,
});
</script>
