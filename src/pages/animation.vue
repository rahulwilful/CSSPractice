<style>
.body {
  background: #000;
  width: 100%;
  height: 100vh;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.btn {
  background: blue;
  padding: 1rem 2rem;
  border: 1px solid white;
  /* animation-name: slideInLeft;
  animation-duration: 2s; */

  /*  animation-timing-function: ease-out; */ /* ease-in, ease-in-out , linear */
  /*  animation-delay: 1s;
  animation-iteration-count: 1; */
  /* animation-direction: normal;  */ /* normal,reverse */
  /*  animation-fill-mode: backwards ;*/ /* forwards ,backwards,both */
  /*   transform: translateX(-150px); */
}

.btn:hover {
  background: rgb(2, 132, 253);
  padding: 1rem 2rem;
  border: 1px solid white;
  transition-property: transform;
  transition-duration: 0.3s;
  transition-timing-function: ease;
  transition-delay: 0s;
  transform: translateY(-10px);
  box-shadow: 0px 0px 10px 1px rgb(255, 187, 0); /* Adjust values as needed */
}

.animate {
  animation-duration: 1s;
  animation-fill-mode: both;
}

.animate.animate-infinite {
  animation-iteration-count: infinite;
}

.animate.animate-delay-1s {
  animation-delay: 1s;
}

.animate.animate-fast {
  animation-duration: 3s;
}

.animate.animate-slow {
  animation-duration: 3s;
}

.slideInLeft {
  animation: slideInLeft 1s ease-in;
}

@keyframes slideInLeft {
  from {
    transform: translateX(-50vw);
  }

  to {
    transform: translate(0);
  }
}

.slideInRight {
  animation: slideInRight 1s ease-in;
}

@keyframes slideInRight {
  from {
    transform: translateX(50vw);
  }

  to {
    transform: translate(0);
  }
}

.slideInTop {
  animation: slideInTop 1s ease-in;
}

@keyframes slideInTop {
  from {
    transform: translateY(-50vh);
  }

  to {
    transform: translate(0);
  }
}

.rotateX {
  animation-name: rotateX;
  animation-timing-function: linear;
  transform-origin: center;
}

@keyframes rotateX {
  from {
    transform: rotateX(0);
  }
  to {
    transform: rotateX(-360deg);
  }
}

.rotateY {
  animation-name: rotateY;
  animation-timing-function: linear;
  transform-origin: center;
}

@keyframes rotateY {
  from {
    transform: rotateY(0);
  }
  to {
    transform: rotateY(-360deg);
  }
}

.rotate {
  animation-name: rotate;
  animation-timing-function: linear;
  transform-origin: center;
}

@keyframes rotate {
  from {
    transform: rotate(0);
  }
  to {
    transform: rotate(-360deg);
  }
}

.bounce {
  animation-name: bounce;
  animation-timing-function: ease-in;
}
@keyframes bounce {
  0%,
  30% {
    transform: translateY(-50vh);
  }

  35%,
  50%,
  70%,
  85%,
  100% {
    transform: translateY(0);
  }
  40% {
    transform: translateY(-6vh);
  }

  60% {
    transform: translateY(-4vh);
  }

  80% {
    transform: translateY(-1vh);
  }

  /*  0% {
    transform: translateY(-50vh);
  }
  30% {
    transform: translateY(-50vh);
  }
  35% {
    transform: translateY(0);
  }
  40% {
    transform: translateY(-6vh);
  }
  50% {
    transform: translateY(0);
  }

  60% {
    transform: translateY(-4vh);
  }
  70% {
    transform: translateY(0);
  }
  80% {
    transform: translateY(-1vh);
  }
  85% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(0);
  } */
}
</style>

<template>
  <div class="body vh-100 d-flex justify-content-center align-items-center">
    <!--     <h1 class="text-light" style="text-shadow: 0px 0px 10px rgba(255, 2, 150, 0.9)">Animation</h1>
 -->
    <div class="flex-column">
      <!--  <button type="button" class="btn m-3 slideInLeft animate animate-slow animate-delay-1s" style="background: blue">Primary</button>
      <button type="button" class="btn m-3 slideInTop animate animate-slow animate-delay-1s" style="background: rgb(0, 255, 76)">Primary</button>
      <button type="button" class="btn m-3 slideInRight animate animate-slow animate-delay-1s" style="background: rgb(255, 0, 0)">Primary</button> -->
      <!-- <button type="button" class="btn m-3 rotateX animate animate-fast animate-infinite animate-delay-1s" style="background: blue">Primary</button>
      <button type="button" class="btn m-3 rotateY animate animate-fast animate-infinite animate-delay-1s" style="background: rgb(0, 255, 76)">Primary</button>
      <button type="button" class="btn m-3 rotate animate animate-infinite animate-fast animate-delay-1s" style="background: rgb(255, 0, 0)">Primary</button> -->
      <button type="button" class="btn m-3 bounce animate animate-slow" style="background: blue">Primary</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Animation",
};
</script>
