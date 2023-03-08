<template>
  <div class="q-pa-md">
    <q-expansion-item
      class="shadow-1 overflow-hidden"
      style="border-radius: 30px; width: 100%"
      icon="explore"
      :label="'Items in Shop $' + subTotal"
      header-class="bg-primary text-white"
      expand-icon-class="text-white"
    >
      <q-card>
        <CardShop
          v-for="(item, index) in items"
          :img="item.url"
          :description="item.description"
          :value="item.value"
          :key="index"
        ></CardShop>
        <q-card-section class="flex justify-between items-end">
          <q-input
            square
            outlined
            v-model="text"
            label="Disscunt"
            :dense="true"
          />
          <q-btn color="primary" style="width: 90px">
            <div class="ellipsis">Apply</div>
          </q-btn>
        </q-card-section>
        <q-card-section class="flex justify-between items-end"
          ><p>Subtotal:</p>
          <p>{{ subTotal }}</p></q-card-section
        >
        <q-card-section class="flex justify-between items-end"
          ><p>Shipping:</p>
          <p v-if="Shipping != 0">{{ Shipping }}</p>
          <p v-else>---</p></q-card-section
        >
        <q-card-section class="flex justify-between items-end"
          ><p>Disccount:</p>
          <p v-if="Disccount != 0">{{ Disccount }}</p>
          <p v-else>---</p></q-card-section
        >
        <q-separator inset />
        <q-card-section class="flex justify-between items-end"
          ><p>Total</p>
          <p>{{ subTotal }}</p></q-card-section
        >
      </q-card>
    </q-expansion-item>
  </div>
</template>
<script>
import CardShop from "./CardShop.vue";

export default {
  components: {
    CardShop: CardShop,
  },
  data() {
    return {
      items: [
        {
          url: require("src/assets/img/Rectangle-4161-52px(3).png"),
          description: "Nike Sneakers",
          value: 69.0,
        },
        {
          url: require("src/assets/img/Rectangle-4161-52px(4).png"),
          description: "Nike Sneakers",
          value: 69.0,
        },
        {
          url: require("src/assets/img/Rectangle-4161-52px(5).png"),
          description: "Nike Sneakers",
          value: 69.0,
        },
      ],
      subTotal: 0,
      Shipping: 0,
      Disccount: 0,
      code: "",
    };
  },
  methods: {
    SubTotal() {
      this.items.length;
      for (let index = 0; index < this.items.length; index++) {
        this.subTotal += this.items[index].value;
        console.log(this.subTotal);
      }
    },
  },
  created() {
    this.SubTotal();
  },
};
</script>
