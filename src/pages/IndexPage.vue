<template>
  <q-page class="row items-center justify-evenly"> </q-page>
</template>

<script setup lang="ts">
import { Countries } from 'countrykit';

import { onMounted } from 'vue';

onMounted(() => {
  console.log(Countries.getByAlpha2('US'));
});
</script>
