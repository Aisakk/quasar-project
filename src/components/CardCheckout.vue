<template>
  <q-card>
    <q-card class="my-card">
      <div class="text-h6 q-ml-md flex items-center">
        <h2 class="">Express Checkout</h2>
      </div>
      <q-card-section class="flex wrap">
        <q-btn
          :style="{ backgroundColor: item.color }"
          style="width: 150px"
          v-for="(item, index) in img"
          :key="index"
          class="q-ml-sm q-mt-sm"
          @click="link(item.href)"
        >
          <div class="flex items-center">
            <img :src="item.url" :alt="item.alt" />
          </div>
        </q-btn>
      </q-card-section>
    </q-card>
  </q-card>
</template>
<script>
export default {
  data() {
    return {
      img: [
        {
          url: require("src/assets/img/ShopPay - White 1pay.svg"),
          alt: "img-2",
          color: "#5A31F4",
          href: "shop.app",
        },
        {
          url: require("src/assets/img/pay.svg"),
          alt: "img-1",
          color: "#F6C657",
          href: "paypal.com",
        },
        {
          url: require("src/assets/img/svgexport-1 (7) 1pay.svg"),
          alt: "img-3",
          color: "#000000",
          href: "pay.google.com",
        },
      ],
    };
  },
  methods: {
    link(value) {
      return window.open(`https://${value}`, "_blank");
    },
  },
};
</script>
