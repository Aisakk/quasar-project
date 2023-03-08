<template>
  <q-card flat bordered class="my-card">
    <q-card-section class="flex items-end q-mt-sm">
      <q-icon :name="fasCashRegister" size="42px"></q-icon>
      <div class="q-ml-sm">30 days satisfaction Guareantee with money back</div>
    </q-card-section>

    <q-separator inset />

    <q-card-section class="q-pt-none flex items-end q-mt-sm">
      <q-icon :name="fasTruck" size="42px"></q-icon>
      <div class="q-ml-sm">Over 38,957 successfully shipped orders</div>
    </q-card-section>
  </q-card>
</template>
<script>
import { fasTruck, fasCashRegister } from "@quasar/extras/fontawesome-v5";

export default {
  created() {
    this.fasTruck = fasTruck;
    this.fasCashRegister = fasCashRegister;
  },
};
</script>
<style lang="scss"></style>
