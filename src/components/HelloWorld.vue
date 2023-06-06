<template>
  <div class="default">
   
    <div class="animation-image1 panel">
      <transition
        appear
        @before-enter="beforeEnter1"
        @enter="enter1"
        @after-enter="afterEnter"
      >
        <img alt="Vue logo" src="../assets/animation-sample1.png" />
      </transition>
    </div>
    
    <div class="animation-image2 panel">
      <transition
        appear
        @before-enter="beforeEnter2"
        @enter="enter2"
        @after-enter="afterEnter"
      >
        <img alt="Vue logo" src="../assets/animation-sample2.png" />
      </transition>
    </div>
    <div class="animation-image3 panel">
      <transition
        appear
        @before-enter="beforeEnter3"
        @enter="enter3"
        @after-enter="afterEnter"
      >
        <img alt="Vue logo" src="../assets/animation-sample3.png" />
      </transition>
    </div>
    <footer>
      <transition-group
        appear
        tag="ul"
        @before-enter="beforeEnterGroup"
        @enter="enterGroup"
      >
        <li v-for="(icon, index) in icons" :key="icon.name" :data-index="index">
          <span class="material-icons">{{ icon.name }}</span>
          <div>{{ icon.text }}</div>
        </li>
      </transition-group>
    </footer>
  </div>
</template>

<script>
import gsap from "gsap";
import { ref } from "vue";
import { ScrollTrigger } from "gsap/ScrollTrigger";

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    var defaultSides = 10;
    var stats = Array.apply(null, { length: defaultSides }).map(function () {
      return 100;
    });
    return {
      visible: false,
      visible1: false,
      stats: stats,
      charax: 300,
      sides: defaultSides,
      minRadius: 50,
      interval: null,
      updateInterval: 500,
    };
  },
  watch: {
    sides: function (newSides, oldSides) {
      var sidesDifference = newSides - oldSides;
      if (sidesDifference > 0) {
        for (var i = 1; i <= sidesDifference; i++) {
          this.stats.push(this.newRandomValue());
        }
      } else {
        var absoluteSidesDifference = Math.abs(sidesDifference);
        for (i = 1; i <= absoluteSidesDifference; i++) {
          this.stats.shift();
        }
      }
    },
    // stats: function (newStats) {
    //   TweenLite.to(this.$data, this.updateInterval / 1000, {
    //     points: generatePoints(newStats),
    //   });
    // },
    updateInterval: function () {
      this.resetInterval();
    },
  },
  setup() {
    gsap.registerPlugin(ScrollTrigger);
    let sections = gsap.utils.toArray(".panel");
    const icons = ref([
      { name: "alternare_email", text: "aaa" },
      { name: "alternare_email", text: "aaa" },
      { name: "alternare_email", text: "aaa" },
      { name: "alternare_email", text: "aaa" },
      { name: "alternare_email", text: "aaa" },
      { name: "alternare_email", text: "aaa" },
      { name: "alternare_email", text: "aaa" },
    ]);
    const beforeEnter = (el) => {
      console.log("aaa");
      el.style.transform = "translateY(-60px)";
      el.style.opacity = 0;
    };
    const beforeEnter1 = (el) => {
      console.log("aaa1");
      el.style.transform = "translateY(-60px)";
      el.style.opacity = 0;
    };
    const beforeEnter2 = (el) => {
      console.log("aaa2");
      el.style.transform = "translateY(-60px)";
      el.style.opacity = 0;
    };
    const beforeEnter3 = (el) => {
      console.log("aaa3");
      el.style.transform = "translateY(-60px)";
      el.style.opacity = 0;
    };
    const enter = (el) => {
      gsap.to(el, {
        scrollTrigger: {
          trigger: ".animation-image",
          toggleActions: "play restart reverse restart",
        },
        duration: 3,
        rotation: 360,
        y: 0,
        opacity: 1,
        ease: "bounce.out",
      });
    };
    const enter1 = (el) => {
      gsap.to(el, {
        // yPercent: -100 * (sections.length - 1),
        scrollTrigger: {
          trigger: ".animation-image1",
          toggleActions: "play restart reverse restart",
          start: "700px 80%",
          end: "+=100",
          snap: 1 / (sections.length - 1),
          markers: true,
        },
        duration: 3,
        rotation: 360,
        y: 0,
        opacity: 1,
        ease: "bounce.out",
      });
    };
    const enter2 = (el) => {
      gsap.to(el, {
        // yPercent: -100 * (sections.length - 1),

        scrollTrigger: {
          trigger: ".animation-image2",
          toggleActions: "play restart reverse restart",
          start: "200px 80%",
          end: "+=100",
          snap: 1 / (sections.length - 1),
          markers: true,
        },
        duration: 3,
        rotation: 360,
        y: 0,
        opacity: 1,
        ease: "bounce.out",
      });
    };
    const enter3 = (el) => {
      gsap.to(el, {
        // yPercent: -100 * (sections.length - 1),
        scrollTrigger: {
          trigger: ".animation-image3",
          toggleActions: "play restart reverse restart",
          start: "200px 80%",
          end: "+=100",
          snap: 1 / (sections.length - 1),

          markers: true,
        },
        duration: 3,
        rotation: 360,
        y: 0,
        opacity: 1,
        ease: "bounce.out",
      });
    };

    const afterEnter = () => {
      console.log("afterEnter");
    };

    const beforeEnterGroup = (el) => {
      console.log("aaa");
      el.style.transform = "translateY(100px)";
      el.style.opacity = 0;
    };
    const enterGroup = (el, done) => {
      gsap.to(el, {
        duration: 1,
        y: 0,
        opacity: 1,
        // ease: "bounce.out",
        onComplete: done,
        delay: el.dataset.index * 0.5,
      });
    };
    return {
      icons,
      beforeEnter,
      beforeEnter1,
      beforeEnter2,
      beforeEnter3,
      enter,
      enter1,
      enter2,
      enter3,
      afterEnter,
      beforeEnterGroup,
      enterGroup,
    };
  },
  mounted() {
    this.resetInterval();
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
body {
  margin: 0;
  padding: 0;
  position: relative;
}
header {
  width: 100%;
  background: #ccdd33;
}
footer {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 100px;
  background: #000000;
}
.center {
  position: absolute;
  width: 30px;
  height: 30px;
  /* left: -15px;
  top: -15px; */
  border-radius: 30px;
  background-color: #ffe683;
}
@keyframes rotate {
  0% {
    transform: rotate(0deg) scale(0);
  }
  100% {
    transform: rotate(360deg) scale(1);
  }
}
svg {
  display: block;
}
polygon {
  fill: #41b883;
}
circle {
  fill: transparent;
  stroke: #35495e;
}
input[type="range"] {
  display: block;
  width: 100%;
  margin-bottom: 15px;
}
.route-enter-from {
  opacity: 0;
  transform: translateX(100px);
}
.route-enter-active {
  transition: ass 0.3s ease-out;
}
.route-leave-to {
  opacity: 0;
  transform: translateX(-100px);
}
.route-leave-active {
  transition: ass 0.3s ease-out;
}
.animation-image {
  top: 0;
}
.animation-image1 {
  top: 0;
  padding-top: 0px;
}
.animation-image2 {
  padding-top: 200px;
}
.animation-image3 {
  /* margin-top: 200px; */
}
.panel {
  height: 0%;
  width: 1000px;
}
</style>
