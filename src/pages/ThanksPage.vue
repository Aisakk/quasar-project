<template>
  <q-page class="flex column">
    <div class="row">
      <div class="col-xs-12 col-sm-12 col-md-6">
        <q-card class="column justify-center items-center q-mt-md">
          <q-card-section>
            <img :src="url" alt="completed" />
          </q-card-section>
          <q-card-section class="column items-center">
            <p>Thank you</p>
            <p>Your order #15636561 has been placed</p>
            <q-btn color="primary" @click="backToIndex">
              <div class="ellipsis">Back to shop</div>
            </q-btn>
          </q-card-section>
        </q-card>
        <div class="col-xs-12 col-sm-12 col-md-6">
          <q-card
            class="column justify-center q-mt-md"
            style="background: #f1f3f6"
          >
            <q-card-section class="flex">
              <div class="p">name:</div>
              <div class="p">Oleo Bone</div>
            </q-card-section>
            <q-separator dark inset style="border: 1px solid #d6d8ea" />
            <q-card-section class="flex">
              <div class="p">email:</div>
              <div class="p">OleoBone@gmail.com</div>
            </q-card-section>
            <q-separator dark inset style="border: 1px solid #d6d8ea" />
            <q-card-section class="flex">
              <div class="p">Ship top:</div>
              <div class="p">4140 Parker Rd. Allentown, New Mexico 31134</div>
            </q-card-section>
            <q-separator dark inset style="border: 1px solid #d6d8ea" />
            <q-card-section class="flex">
              <div class="p">Bil to:</div>
              <div class="p">4140 Parker Rd. Allentown, New Mexico 31134</div>
            </q-card-section>
            <q-separator dark inset style="border: 1px solid #d6d8ea" />
            <q-card-section class="flex">
              <div class="p">payment:</div>
              <div class="p">Credit Card</div>
            </q-card-section>
          </q-card>
        </div>
      </div>
      <div class="col-md-6 q-mt-md" id="summarycard">
        <summary-card-vue class="q-ml-lg"></summary-card-vue>
      </div>
    </div>
  </q-page>
</template>
<script>
import SummaryCardVue from "src/components/SummaryCard.vue";

export default {
  components: {
    SummaryCardVue: SummaryCardVue,
  },
  data() {
    return {
      url: require("src/assets/img/Order_complete_1_.svg"),
    };
  },
  methods: {
    backToIndex() {
      this.$router.push("/");
    },
  },
};
</script>
<style lang="scss">
.q-page {
  margin: 0px 16px 0px 16px;
}
@media (max-width: 768px) {
  #summarycard {
    display: none;
  }
}
</style>
