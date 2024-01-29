<style scoped>
.main {
  background-size: cover;
  background-repeat: no-repeat;
  background-attachment: fixed;
  width: 100%;
  height: 100vh;
  transition: background 1.5s ease;
}
.container {
  height: 90vh;
}

@media (max-width: 576px) {
  .main {
    height: auto; /* Adjust height for small screens */
  }
}

#carouselExampleControls {
  overflow-x: auto;
}

/* Add this style to ensure slides stay on the same line */
.carousel-inner {
  white-space: nowrap;
}

/* Add these styles to adjust the layout of individual slides and cards */
.carousel-item {
  width: 100%; /* Adjust the width as needed */
  display: flex;
  flex-direction: row;
}

.cards-wrapper {
  display: flex;
  flex-direction: row;
}

.card {
  margin: 0.5rem;
  width: 100%; /* Adjust the width as needed */
}

.image-wrapper {
  height: 5rem;
  width: 100%; /* Adjust the width as needed */
}

.image-wrapper img {
  max-width: 100%;
  max-height: 100%;
}
</style>

<template>
  <div class="vh-100">
    <div class="main" :style="{ 'background-image': 'url(' + items[imageIndex].imageUrl + ')' }">
      <div class="vh-100">
        <div class="container-fluid">
          <div class="row gx-1">
            <div class="col" v-for="(progress, i) in progressBars" :key="i">
              <div class="progress bg-secondary mt-1" :style="{ height: '3px', marginBottom: '5px' }">
                <div class="progress-bar" role="progressbar" :style="{ width: progress + '%' }" aria-valuenow="0" aria-valuemin="0" aria-valuemax="100"></div>
              </div>
            </div>
          </div>
          <div>
            <div class="container3 justify-content-center bg-light align-items-center pt-3">
              <ol style="max-height: 250px; overflow-y: auto">
                <li v-for="day in itinerary" :key="day" class="bg-transparent text-dark mb-2" style="background-color: rgba(255, 255, 255, 0.7); border-radius: 8px">
                  <h4>{{ Object.keys(day)[0] }}</h4>
                  <ul>
                    <li v-for="line in Object.values(day)[0]" :key="line" class="bg-transparent">
                      <span v-html="highlightWords(line)"></span>
                    </li>
                  </ul>
                </li>
              </ol>
            </div>
            <div class="p-2">
              <div class="p-2 position-absolute bottom-0 end-0">
                <button @click="saveToItinerarys" type="button" class="btn btn-secondary btn-sm">Save1</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Body2",
  data() {
    return {
      name_entity: ["word221", "word123", "word332", "word121", "word122", "word133", "word331", "word332", "word333"],
      activities: ["Breakfast:", "Morning Activity:", "Lunch:", "Evening Activity:", "Night:"],
      loadingPercentage: 0,
      activeIndex: 0,
      slides: [],
      itinerary: [],
      imageIndex: 0,
      items: [{ imageUrl: "/src/assets/body/pexels-artem-saranin-1214011.jpg" }, { imageUrl: "/src/assets/body/pexels-dillon-kydd-11523148.jpg" }, { imageUrl: "/src/assets/body/pexels-james-wheeler-1539225.jpg" }, { imageUrl: "/src/assets/body/pexels-mayur-sable-13612812.jpg" }],
      progressBars: [0, 0, 0, 0],
      rawItinerary:
        "\n\nDay 1: \n1. Breakfast: word111 word112 word113\n2. Morning Activity: word121 word122 word123\n3. Lunch: word131 word132 word133\n\nDay 2: \n1. Evening Activity: word211 word212 word213\n2. Night: word221 word222 word223\n3. Breakfast: word231 word232 word233\n\nDay 3: \n1.Evening Activity: word311 word312 word313\n2. Morning Activity: word321 word322 word323\n3. Lunch: word331 word332 word333",
    };
  },
  created() {
    /* console.log("raw itinerary", this.rawItinerary); */
    const tempItinerary1 = this.rawItinerary.split("\n\n");
    var tempItinerary2 = [];
    var tempItinerary3 = [];
    var transformedItinerary = {};

    for (var day of tempItinerary1) {
      day = day
        .replace(/\\n/g, "\n")
        .replace(/\\t/g, "")
        .replace(/(\d+\.\s+)/g, (match) => match.trim());

      if (day.length > 0) {
        const tempItinerary = day.split("\n");
        var tempDay = {};
        tempDay["breakfast"] = "";
        tempDay["morning activity"] = "";
        tempDay["lunch"] = "";
        tempDay["evening activity"] = "";
        tempDay["night"] = "";

        for (var j = 1; j < tempItinerary.length; j++) {
          const activityMatch = this.activities.find((activity) => tempItinerary[j].toLowerCase().includes(activity.toLowerCase()));

          if (activityMatch) {
            // Extract activity value and assign to corresponding property
            tempDay[activityMatch.toLowerCase()] = tempItinerary[j].replace(activityMatch, "").trim();
          }
        }

        // Check if any activity has a non-empty value before adding to the transformedItinerary
        if (Object.values(tempDay).some((value) => value !== "")) {
          transformedItinerary[tempItinerary[0].trim()] = tempDay;
        }
      }
    }

    // Convert the transformedItinerary object to an array
    this.itinerary = Object.entries(transformedItinerary).map(([day, activities]) => ({
      [day]: activities,
    }));
    console.log("sub day itinerary", this.itinerary);
    //this.chunkNameEntity();
    //converting each line of day to words of array
  },
  mounted() {
    this.startProgress();
  },
  methods: {
    highlightWords(line) {
      const wordsToHighlight = this.name_entity;
      return line
        .split(/\b/)
        .map((word) => (wordsToHighlight.includes(word.trim()) ? `<span style="background-color: yellow">${word}</span>` : word))
        .join("");
    },

    chunkNameEntity() {
      const chunkSize = 6; // Number of entities per slide
      for (let i = 0; i < this.name_entity.length; i += chunkSize) {
        this.slides.push(this.name_entity.slice(i, i + chunkSize));
      }
    },

    async handleSubmit() {},
    startProgress() {
      setInterval(() => {
        this.loadingPercentage += 5;
        this.progressBars[this.activeIndex] = this.loadingPercentage;
        if (this.loadingPercentage > 105) {
          this.loadingPercentage = 0;
          this.progressBars[this.activeIndex] = 0;
          /*  console.log("progressbar", this.progressBars.length);
          console.log("activeindex", this.activeIndex); */
          if (this.activeIndex < this.progressBars.length - 1) {
            // Change the background image to the next one
            this.imageIndex = (this.imageIndex + 1) % this.items.length;
            // Move to the next progress bar
            this.activeIndex++;
          } else {
            this.imageIndex = (this.imageIndex + 1) % this.items.length;
            // Reset to the first progress bar
            this.activeIndex = 0;
          }
        }
      }, 200);
    },
  },
};
</script>
