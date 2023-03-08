<template>
  <q-page class="flex column">
    <div class="row">
      <div class="col-xs-12 col-sm-12 col-md-12">
        <div class="col-xs-12 col-sm-12 -col-md-12 title">
          <h2>Checkout</h2>
        </div>
        <div class="col-xs-12 col-sm-12 -col-md-12" id="mobile">
          <CollapseSummary></CollapseSummary>
          <CardInfo class="q-mt-md"></CardInfo>
          <CardInfoFireVue class="q-mt-md"></CardInfoFireVue>
          <CardCheckout class="q-mt-md"></CardCheckout>
          <StepperPayment></StepperPayment>
        </div>

        <div class="row" id="desktop">
          <div class="col-md-7">
            <CardInfoFireVue class="q-mt-md"></CardInfoFireVue>
            <CardCheckout class="q-mt-md"></CardCheckout>
            <StepperPayment></StepperPayment>
          </div>
          <div class="q-ml-md col-md-4">
            <summary-card-vue></summary-card-vue>
            <CardInfo class="q-mt-md"></CardInfo>
          </div>
        </div>
      </div>
    </div>
  </q-page>
</template>
<style lang="scss">
//$
.q-page {
  margin: 0px 16px 0px 16px;
}
.title h2 {
  font-size: 32px;
  color: $primary;
  font-weight: 700;
  color: #000034;
  line-height: 40px;
  width: 150px;
  height: 40px;
}
@media (max-width: 768px) {
  #desktop {
    display: none;
  }
}
@media (min-width: 769px) {
  #mobile {
    display: none;
  }
}
</style>
<script>
import { defineComponent } from "vue";
import CollapseSummary from "src/components/CollapseSummary.vue";
import CardInfo from "src/components/CardInfo.vue";
import CardCheckout from "src/components/CardCheckout.vue";
import CardInfoFireVue from "src/components/CardInfoFire.vue";
import StepperPayment from "src/components/StepperPayment.vue";
import SummaryCardVue from "src/components/SummaryCard.vue";

export default defineComponent({
  components: {
    CollapseSummary: CollapseSummary,
    CardInfo: CardInfo,
    CardCheckout: CardCheckout,
    CardInfoFireVue: CardInfoFireVue,
    StepperPayment: StepperPayment,
    SummaryCardVue: SummaryCardVue,
  },
  name: "IndexPage",
});
</script>
