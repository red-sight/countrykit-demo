<template>
  <q-page class="row q-gutter-md q-pa-lg">
    <q-card
      v-for="country in state.countries"
      :key="country.iso2"
      class="country-card col-xs-12 col-sm-6 col-md-4 col-lg-2"
    >
      <q-item>
        <q-item-section avatar v-if="country">
          <q-avatar square>
            <img :src="country?.flags?.['1x1']" />
          </q-avatar>
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ country?.name }}</q-item-label>
          <q-item-label caption
            >{{ country?.continent }}/{{ country?.subregion }}</q-item-label
          >
        </q-item-section>
        <q-item-section side>
          <q-chip></q-chip>
        </q-item-section>
      </q-item>
    </q-card>
  </q-page>
</template>

<script setup lang="ts">
import { Countries, ICountry } from 'countrykit';

import { onMounted, reactive } from 'vue';

const state = reactive<{
  country: ICountry | undefined;
  countries: ICountry[];
}>({
  country: undefined,
  countries: []
});

onMounted(() => {
  state.country = Countries.getByISO2('RU');
  console.log(state.country);
  state.countries = Countries.getAll();
});
</script>

<style lang="sass">
.country-card
  max-width: 380px
</style>
