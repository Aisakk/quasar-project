<template>
  <div class="q-pa-md">
    <div class="row">
      <q-carousel animated v-model="slide" arrows navigation infinite>
        <q-carousel-slide
          v-for="(item, index) in img"
          :name="index"
          :img-src="item.url"
          :key="index"
        />
      </q-carousel>
    </div>
    <div class="row">
      <div class="col">
        <q-card class="my-card q-mt-md">
          <q-card-section class="column justify-center items-center">
            <div class="container-price flex">
              <p style="font-weight: 500; font-size: 20px; line-height: 30px">
                Price:
              </p>
              <p style="font-weight: 600; font-size: 30px; line-height: 40px">
                $ {{ total }}
              </p>
              <p
                style="background: #eff0f5; border-radius: 8px"
                class="flex justify-center items-center q-ml-md"
              >
                -{{ disccount }}%
              </p>
            </div>
          </q-card-section>
          <q-card-section class="flex justify-center items-center">
            <div
              class="container-group flex justify-around items-center"
              style="width: 70%; height: 80px"
            >
              <p
                style="
                  font-weight: 500;
                  font-size: 20px;
                  line-height: 30px;
                  color: #4b4e68;
                "
              >
                Quantite
              </p>
              <q-btn
                style="width: 30px; height: 30px"
                round
                color="primary"
                label="-"
                @click="decrementProduct"
              />
              {{ product }}
              <q-btn
                style="width: 30px; height: 30px"
                round
                color="primary"
                label="+"
                @click="incrementProduct"
              />
            </div>
          </q-card-section>
        </q-card>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <div class="container-text q-mt-md">
          <p
            style="
              font-style: normal;
              font-weight: 500;
              font-size: 18px;
              line-height: 28px;
            "
          >
            Quis tincidunt nunc suscipit egestas. Viverra erat cras ullamcorper
            amet. Risus velit tempus at eu. Eu facilisi tempor ipsum orci
            placerat urna pretium adipiscing dignissim. Risus dolor fringilla
            diam nulla iaculis. Odio nunc nulla malesuada sed vulputate nisl
            metus sem. Elit pulvinar in auctor ac vitae morbi et. Nulla
            malesuada consequat arcu semper cras pharetra fermentum. Nisl eu
            arcu libero etiam diam. Scelerisque cum pharetra amet nulla sed
            nulla mauris tortor. Magna elementum montes eget ullamcorper id diam
            dui pellentesque. Eget mi in tempor amet vitae.
          </p>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col-md-6 col-xs-12">
        <q-card
          class="column justify-center items-center"
          style="height: 140px"
        >
          <q-card-section>
            <div class="container-group flex">
              <q-icon name="lock" size="24px" style="color: #84849a"></q-icon>
              <p class="content-end" style="color: #84849a">
                Guaranteed Safe & Secure Checkout
              </p>
            </div>
          </q-card-section>
          <q-card-section>
            <img
              :src="img.url"
              v-for="(img, index) in imgGroup"
              :key="index"
              class="q-ml-md"
            />
          </q-card-section>
        </q-card>
      </div>
      <div class="col-md-6 col-xs-12">
        <q-card style="height: 140px">
          <q-card-section class="flex justify-center items-center">
            <q-icon name="support_agent" size="72px"></q-icon>
            <p
              class="flex align-items"
              style="
                width: 80px;
                font-weight: 600;
                font-size: 20px;
                line-height: 30px;
              "
            >
              24/7Supportt
            </p>
          </q-card-section>
        </q-card>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <div class="container-botton column q-mt-md items-center">
          <q-btn color="primary" @click="linkThanks" style="width: 170px">
            <div class="ellipsis">Yes, I Want</div>
          </q-btn>

          <q-btn
            flat
            @click="linkToBack"
            color="primary"
            label="No, thanks"
            class="q-ml-md"
            style="width: 170px"
          />
        </div>
      </div>
    </div>
  </div>
</template>
<style lang="scss">
.q-carousel {
  width: 100%;
}
</style>
<script>
import { ref } from "vue";
import { useRouter } from "vue-router";
export default {
  setup() {
    let product = ref(0);
    let price = ref(50);
    let total = ref(0);
    let disccount = ref(10);
    const router = useRouter();

    function incrementProduct() {
      product.value++;
      total.value =
        price.value * product.value -
        price.value * product.value * (disccount.value / 100);
    }
    function decrementProduct(disccountValue) {
      product.value--;
      total.value =
        price.value * product.value -
        price.value * product.value * (disccount.value / 100);
    }
    function linkThanks() {
      router.push("thanks");
    }
    function linkToBack() {
      router.push("/");
    }
    return {
      product,
      slide: ref(1),
      img: [
        {
          id: 1,
          url: require("src/assets/img/shoots.png"),
        },
        {
          id: 2,
          url: require("src/assets/img/shoots.png"),
        },
        {
          id: 3,
          url: require("src/assets/img/shoots.png"),
        },
      ],
      imgGroup: [
        {
          url: require("src/assets/img/Group 39655.png"),
        },
        {
          url: require("src/assets/img/Group 39654.png"),
        },
        {
          url: require("src/assets/img/Group 39653.png"),
        },
        {
          url: require("src/assets/img/Group 39656.png"),
        },
        {
          url: require("src/assets/img/Group 39652.png"),
        },
        {
          url: require("src/assets/img/Group 39658.png"),
        },
      ],
      price: ref(50),
      total,
      disccount,
      incrementProduct,
      decrementProduct,
      linkThanks,
      linkToBack,
    };
  },
};
</script>
