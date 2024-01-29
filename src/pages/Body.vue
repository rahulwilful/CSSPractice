<template>
  <div>
    <div id="carouselExampleCaptions" class="carousel slide" data-bs-ride="carousel" ref="carousel">
      <div class="carousel-indicators">
        <button v-for="(item, index) in items" :key="index" type="button" :data-bs-target="'#carouselExampleCaptions'" :data-bs-slide-to="index" :class="{ active: index === activeIndex }" @click="goTo(index)"></button>
      </div>
      <div class="carousel-inner">
        <div v-for="(item, index) in items" :key="index" class="carousel-item" :class="{ active: index === activeIndex }">
          <!-- New row for progress bars -->
          <!-- Image and caption -->
          <img :src="item.imageUrl" class="d-block w-100" alt="..." />
          <div class="carousel-caption d-none d-md-block">
            <div class="mt-0">
              <div class="row">
                <div class="col" v-for="(progress, i) in progressBars" :key="i">
                  <div class="progress bg-secondary" :style="{ height: '5px' }">
                    <div class="progress-bar" role="progressbar" :style="{ width: progress + '%' }" aria-valuenow="0" aria-valuemin="0" aria-valuemax="100"></div>
                  </div>
                </div>
              </div>
            </div>
            <!-- <h5 class="shadow-lg">Well Come To NavBar</h5>
            <p class="shadow-lg">Best Web Development IT Company In India</p>
            <button class="btn btn-primary shadow-lg">Technology</button>
            <button class="btn btn-danger shadow-lg">Web Development</button>
            <button class="btn btn-success shadow-lg">Tech & Fun</button> -->
          </div>
        </div>
      </div>
    </div>C
  </div>
</template>

<script>
export default {
  name: "Body",
  data() {
    return {
      loadingPercentage: 0,
      activeIndex: 0,
      progressBars: [0, 0, 0, 0],
      items: [{ imageUrl: "https://source.unsplash.com/1400x720/?goa,dark" }, { imageUrl: "https://source.unsplash.com/1400x720/?forest,dark" }, { imageUrl: "https://source.unsplash.com/1400x720/?waterfall,dark" }, { imageUrl: "https://source.unsplash.com/1400x720/?fort,dark" }],
    };
  },
  methods: {
    next() {
      this.activeIndex = (this.activeIndex + 1) % this.items.length;
      this.loadingPercentage = 0;
      this.startProgress();
    },
    prev() {
      this.activeIndex = (this.activeIndex - 1 + this.items.length) % this.items.length;
      this.loadingPercentage = 0;
      this.startProgress();
    },
    goTo(index) {
      this.activeIndex = index;
      this.loadingPercentage = 0;
      this.startProgress();body
    },
    startProgress() {
      const intervalId = setInterval(() => {
        this.progressBars[this.activeIndex] += 5;
        if (this.progressBars[this.activeIndex] >= 100) {
          clearInterval(intervalId);
          this.progressBars[this.activeIndex] = 0;
          this.next();
        }
      }, 200);
    },
  },
  mounted() {
    this.startProgress();
  },
};
</script>
