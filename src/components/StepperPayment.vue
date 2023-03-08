<template>
  <div class="q-mt-md">
    <q-stepper v-model="step" header-nav ref="stepper" color="primary" animated>
      <q-step
        :name="1"
        title="Information"
        icon="settings"
        :done="step > 1"
        :header-nav="step > 1"
      >
        <div class="container-group">
          <div class="title-h6">
            <h4 class="title-form">Contact Information</h4>
          </div>
          <div
            class="container-input"
            v-for="(contact, index) in contactInformationStep1"
            :key="index"
          >
            <label class="title-label" for=""> {{ contact.placeholder }}</label>
            <q-input
              outlined
              v-model="contact.name"
              :dense="contact.dense"
              :type="contact.type"
              :rules="contact.rule"
              :placeholder="contact.placeholder"
            >
              <template v-slot:prepend>
                <q-icon :name="contact.icon" />
              </template>
            </q-input>
          </div>
        </div>
        <div class="container-group2">
          <div class="title-h6">
            <h5 class="title-form">Shipping Detail</h5>
          </div>
          <label for="" class="title-label">Country</label>
          <q-select
            outlined
            v-model="model"
            :options="country"
            :dense="true"
            :options-dense="true"
            label="Country"
            class="q-mb-sm"
          >
            <template v-slot:prepend>
              <q-icon name="country" class="justify-end" />
            </template>
          </q-select>
          <div
            class="container-input"
            v-for="(shipping, index) in ShippingDetalStep1"
            :key="index"
          >
            <label class="title-label" for="">{{ shipping.placeholder }}</label>
            <q-input
              outlined
              v-model="shipping.name"
              :dense="shipping.dense"
              :key="index"
              :type="shipping.type"
              :rules="shipping.rule"
              :placeholder="shipping.placeholder"
            >
              <template v-slot:prepend>
                <q-icon :name="shipping.icon" />
              </template>
            </q-input>
          </div>
        </div>

        <q-stepper-navigation>
          <q-btn
            @click="
              () => {
                done1 = true;
                step = 2;
              }
            "
            color="primary"
            label="Continue"
          />
        </q-stepper-navigation>
      </q-step>

      <q-step
        :name="2"
        title="Payment"
        caption="Optional"
        icon="settings"
        :done="step > 2"
        :header-nav="step > 2"
      >
        <div class="container-group-payment q-mb-md">
          <q-btn
            class="q-ml-md"
            outline
            color="primary"
            label="Credit Card"
            icon="credit_card"
          />
          <q-btn
            class="q-ml-md"
            outline
            color="primary"
            label="Paypal"
            icon="paypal"
            @click="paypaylLink"
          />
        </div>
        <div class="container-group-payment2">
          <div
            class="container-group"
            v-for="(pay, index) in payMentStep2"
            :key="index"
          >
            <label class="title-label" for="">{{ pay.placeholder }}</label>
            <q-input
              outlined
              v-model="pay.name"
              :dense="pay.dense"
              :type="pay.type"
              :rules="pay.rule"
            >
              <template v-slot:prepend>
                <q-icon :name="pay.icon" />
              </template>
            </q-input>
          </div>
        </div>
        <div class="container-group-payment3">
          <div class="title-h6">
            <h5 class="title-form">Shipping Details</h5>
          </div>
          <div
            class="container-group"
            v-for="(shippingDetail2, index) in ShippingDetailPaymentStep2"
            :key="index"
          >
            <label class="title-label" for="">
              {{ shippingDetail2.placeholder }}</label
            >
            <q-input
              outlined
              v-model="shippingDetail2.name"
              :dense="shippingDetail2.dense"
              :type="shippingDetail2.type"
              :rules="shippingDetail2.rule"
              :placeholder="shippingDetail2.placeholder"
            >
              <template v-slot:prepend>
                <q-icon :name="shippingDetail2.icon" />
              </template>
            </q-input>
          </div>
        </div>
        <div class="container-group-payment4">
          <q-option-group
            v-model="groupOption"
            :options="optionsGroup"
            color="primary"
          />
          <template v-if="groupOption == 'different shipping'">
            <label for="" class="title-label"> Country</label>
            <q-select
              outlined
              v-model="model"
              :options="country"
              :dense="true"
              :options-dense="true"
              label="Country"
              class="q-mb-sm"
            >
              <template v-slot:prepend>
                <q-icon name="country" class="justify-end" />
              </template>
            </q-select>
            <div
              class="container-group"
              v-for="(billing, index) in BilingAddressStep2"
              :key="index"
            >
              <label class="title-label" for="">
                {{ billing.placeholder }}</label
              >
              <q-input
                outlined
                v-model="billing.name"
                :dense="billing.dense"
                :type="billing.type"
                :rules="billing.rule"
                :placeholder="billing.placeholder"
              >
                <template v-slot:prepend>
                  <q-icon :name="billing.icon" />
                </template>
              </q-input>
            </div>
          </template>
        </div>
        <q-stepper-navigation>
          <q-btn
            flat
            @click="step = 1"
            color="primary"
            label="Back"
            class="q-ml-sm"
          />

          <q-btn @click="pageUpSell" color="primary" label="Finish" />
        </q-stepper-navigation>
      </q-step>
    </q-stepper>
  </div>
</template>
<script>
export default {
  name: "stepper-payment",
  data() {
    return {
      model: "",
      step: 1,
      country: ["EE.UU", "Spain", "Europe", "Australia", "Brasil"],
      contactInformationStep1: [
        {
          name: "",
          field: "email",
          type: "email",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          placeholder: "Email Address",
          icon: "mail",
        },
        {
          name: "",
          type: "text",
          field: "phone",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          placeholder: "Phone Number",
          icon: "phone",
        },
      ],
      ShippingDetalStep1: [
        {
          name: "",
          type: "text",
          field: "firstname",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          placeholder: "First Name",
          icon: "person",
        },
        {
          name: "",
          type: "text",
          field: "lastname",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          placeholder: "Last Name",
          icon: "person",
        },
        {
          name: "",
          type: "text",
          field: "address",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          placeholder: "Address",
          icon: "home",
        },
        {
          name: "",
          type: "text",
          field: "apartment",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          placeholder: "Apartment",
          icon: "apartment",
        },
        {
          name: "",
          type: "text",
          field: "suit",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          placeholder: "Enter your suit",
          icon: "apartment",
        },
        {
          name: "",
          type: "text",
          field: "city",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          placeholder: "city",
          icon: "place",
        },
        {
          name: "",
          type: "text",
          field: "postCode",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          placeholder: "Post Code",
          icon: "approval",
        },
      ],
      payMentStep2: [
        {
          creditNumber: "",
          field: "creditNumber",
          type: "text",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          icon: "credit_card",
          placeholder: "Credit Card Number",
        },
        {
          name: "",
          field: "nameCard",
          type: "text",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          icon: "account_balance_wallet",
          placeholder: "Name of Card",
        },
      ],

      ShippingDetailPaymentStep2: [
        {
          name: "",
          type: "date",
          field: "time",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          icon: "event",
          placeholder: "Expiry Date",
        },
        {
          name: "",
          type: "text",
          field: "securityCode",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          icon: "lock",
          placeholder: "Security Code",
        },
      ],

      BilingAddressStep2: [
        {
          name: "",
          type: "text",
          field: "firstname2",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          icon: "person",
          placeholder: "First Name",
        },
        {
          name: "",
          type: "text",
          field: "lastname2",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          icon: "person",
          placeholder: "Last Name",
        },
        {
          name: "",
          type: "text",
          field: "address2",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          icon: "home",
          placeholder: "Address",
        },
        {
          name: "",
          type: "text",
          field: "apartment2",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          icon: "apartment",
          placeholder: "Apartment",
        },
        {
          name: "",
          type: "text",
          field: "suit2",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          icon: "apartment",
          placeholder: "Suit",
        },
        {
          name: "",
          type: "text",
          field: "city2",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          icon: "place",
          placeholder: "City",
        },
        {
          name: "",
          type: "text",
          field: "postCode2",
          rule: [(val) => !!val || "this field is required"],
          dense: true,
          icon: "approval",
          placeholder: "Post Code",
        },
      ],
      optionsGroup: [
        {
          label: "Same as shipping address",
          value: "shipping",
        },
        {
          label: "Use a different billing address",
          value: "different shipping",
        },
      ],
      groupOption: false,
    };
  },
  methods: {
    paypaylLink() {
      return (window.location.href = "www.paypal.com");
    },
    pageUpSell() {
      this.$router.push("upsell");
    },
  },
};
</script>
<style lang="scss">
.title-label {
  font-weight: 500;
  font-size: 14px;
  line-height: 24px;
  color: #000034;
}
.title-form {
  font-family: "Poppins";
  font-style: normal;
  font-weight: 600;
  font-size: 20px;
  line-height: 30px;

  color: #000034;
}
@media screen {
}
</style>
