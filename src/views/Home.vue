<template>
  <v-app>
    <!-- <v-container class="backgroundImages"> -->
    <img v-for="image in anthonyPics" :src="image" alt="" style="display: none;" />
    <div v-for="image in anthonyPics" :key="image" :style="{ backgroundImage: `url(${image})` }"></div>
    <div class="backgroundImages" v-bind:style='{ backgroundImage: `${this.currentPic}` }'>
      <v-container class="full-height" fluid>
        <div class="crawler">
          <span class="crawler-text">Happy 23rd Birthday Anthony Your buddy max loves you lots pikmin 4 coming in one week
            maybe
            you can come over and we can play it together when it is here would be lots of fun xoxo max</span>
        </div>
        <v-container class="third-height" v-for="styleType in this.celebrationStyles" :celebrationStyle="styleType">
          <ConfettiButton :celebrationStyle="styleType" />
        </v-container>
      </v-container>
      <!-- <v-footer style='z-index:9999999'>
        <SecretButton />
      </v-footer> -->
    </div>
  </v-app>
</template>

<script>
import ConfettiButton from '@/components/ConfettiButton.vue';
import SecretButton from '@/components/SecretButton.vue';
import pic1 from '../assets/anthonyPics/pic1.jpg';
import pic2 from '../assets/anthonyPics/pic2.jpg';
import pic3 from '../assets/anthonyPics/pic3.jpg';
import pic4 from '../assets/anthonyPics/pic4.jpg';
import pic5 from '../assets/anthonyPics/pic5.jpg';
import pic6 from '../assets/anthonyPics/pic6.jpg';
import pic7 from '../assets/anthonyPics/pic7.jpg';
import pic8 from '../assets/anthonyPics/pic8.jpg';
import pic9 from '../assets/anthonyPics/pic9.jpg';
import pic10 from '../assets/anthonyPics/pic10.jpg';
import pic11 from '../assets/anthonyPics/pic11.jpg';
import pic12 from '../assets/anthonyPics/pic12.jpg';
import pic13 from '../assets/anthonyPics/pic13.jpg';
import pic14 from '../assets/anthonyPics/pic14.jpg';
import pic15 from '../assets/anthonyPics/pic15.jpg';


export default {
  components: {
    ConfettiButton,
    SecretButton,
  },
  data() {
    return {
      celebrationStyles: [
        "Like Anthony 👍",
        "Love Anthony ❤️",
        "Colorblind Anthony 🐶",
      ],
      anthonyPics: [pic1, pic2, pic3, pic4, pic5, pic6, pic7, pic8, pic9, pic10, pic11, pic12, pic13, pic14, pic15],
      currentPic: '',
      picNum: 0,
    }
  },
  methods: {
    preload(imgURL) {
      var img = new Image();
      img.src = imgURL;
      return img;
    },
    nextAnthony() {
      let nextPic = this.picNum + 1;
      this.currentPicUrl = this.anthonyPics[nextPic % this.anthonyPics.length];
      let url = `url(${this.currentPicUrl})`;
      this.currentPic = url;
      this.picNum = nextPic;
      // console.log("nextAnthony ", this.currentPic, this.picNum);
    }
  },
  mounted() {
  },
  created() {
    const picNum = Math.floor(Math.random() * this.anthonyPics.length);
    let url = `url(${this.anthonyPics[picNum]})`;
    this.currentPic = url;
    // console.log(this.currentPic);
    this.interval = setInterval(() => this.nextAnthony(), 5000);
  },
}
</script>

<style scoped>
.backgroundImages {
  height: 100vh;
  background-color: black;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  -webkit-transition: all 3s ease;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  -moz-backface-visibility: hidden;
  -ms-backface-visibility: hidden;
  transition: all 3s ease;
  -webkit-transform: translate3d(0, 0, 0);
  transform: translate3d(0, 0, 0);
}

.full-height {
  height: 100%;
}

.third-height {
  height: 30%;
}

.crawler {
  margin: 0 auto;
  overflow: hidden;
  white-space: nowrap;
}

.crawler-text {
  display: inline-block;
  font-family: ka1;
  font-size: 3em;
  white-space: nowrap;
  padding-left: 100%;
  animation: crawl 40s linear infinite;
}

@keyframes crawl {
  0% {
    transform: translateX(0);
  }

  100% {
    transform: translateX(-100%);
  }
}
</style>
