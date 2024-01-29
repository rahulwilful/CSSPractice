<style>
.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: opacity 0.5s, transform 0.5s;
}
.slide-fade-enter,
.slide-fade-leave-to {
  opacity: 0;
  transform: translateX(20px); /* Adjust the value as needed */
}
</style>

<template>
  <div>
    <div class="container-sm container container-md container-lg container-xl container-xxl d-flex align-items-center justify-content-center">
      <div class="row">
        <div class="col-1">
          <button v-if="card1 !== 0" type="button" class="btn bg-transparent" @click="prev">
            <i class="bi bi-chevron-left text-dark"></i>
          </button>
          <button v-else type="button" class="btn bg-transparent">
            <i class="bi bi-chevron-left text-secondary"></i>
          </button>
        </div>
        <div class="col-10">
          <transition name="slide-fade">
            <div class="row flex-row">
              <div class="col" :key="card1">
                <div style="width: 8rem; height: auto">
                  <img :src="imageUrl + images[card1]" alt="" style="width: 8rem; height: auto" />
                </div>
              </div>
              <div class="col" :key="card1 + 1">
                <div style="width: 8rem; height: auto">
                  <img :src="imageUrl + images[card1 + 1]" alt="" style="width: 8rem; height: auto" />
                </div>
              </div>
              <div class="col" :key="card1 + 2">
                <div style="width: 8rem; height: auto">
                  <img :src="imageUrl + images[card1 + 2]" alt="" style="width: 8rem; height: auto" />
                </div>
              </div>
            </div>
          </transition>
        </div>
        <div class="col-1">
          <button v-if="card1 + 2 !== images.length - 1" type="button" class="btn bg-transparent" @click="next">
            <i class="bi bi-chevron-right text-dark"></i>
          </button>
          <button v-else type="button" class="btn bg-transparent">
            <i class="bi bi-chevron-right text-secondary"></i>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SickCarousel",
  data() {
    return {
      card1: 0,
      card2: 0,
      card3: 0,
      imageUrl: "https://source.unsplash.com/1400x720/?",
      images: ["Taj Mahal", "Egyptian Pyramid", "Goa", "Statue Of Liberty", "Great Wall OF China", "Leaning Tower Of Pissa", "Amsterdam", "Mumbai", "Burj Khalifa", "Burj Al Arab"],
    };
  },
  methods: {
    next() {
      if (this.card1 + 2 != this.images.length) {
        this.card1++;
      }
      console.log(this.images.length);
      console.log(this.card1);
    },
    prev() {
      if (this.card1 != 0) {
        this.card1--;
      }
      console.log(this.card1);
    },
  },
};
</script>
