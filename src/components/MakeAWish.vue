<script setup>
import { ref } from 'vue'

const emit = defineEmits(['next'])

const candleBlown = ref(false)
const showConfetti = ref(false)

const confettiPieces = Array.from({ length: 60 }, (_, index) => ({
  id: index,
  left: Math.random() * 100,
  delay: Math.random() * 2,
  duration: 2.5 + Math.random() * 2,
  rotation: Math.random() * 360,
  type: index % 4
}))

const blowCandle = () => {
  if (candleBlown.value) return

  candleBlown.value = true

  setTimeout(() => {
    showConfetti.value = true
  }, 400)
}

const nextPage = () => {
  emit('next')
}
</script>

<template>
  <section class="wish-page">

    <!-- CONFETTI -->

    <div
      v-if="showConfetti"
      class="confetti-container"
    >
      <span
        v-for="piece in confettiPieces"
        :key="piece.id"
        class="confetti"
        :class="`confetti-${piece.type}`"
        :style="{
          left: piece.left + '%',
          animationDelay: piece.delay + 's',
          animationDuration: piece.duration + 's',
          transform: `rotate(${piece.rotation}deg)`
        }"
      ></span>
    </div>


    <div class="wish-card">

      <!-- DECORATION -->

      <div class="corner-star star-one">
        ✦
      </div>

      <div class="corner-star star-two">
        ★
      </div>

      <div class="corner-heart">
        ♡
      </div>


      <!-- TITLE -->

      <div class="wish-header">

        <span class="small-title">
          ✦ BIRTHDAY GIRL ✦
        </span>

        <h1>
          MAKE A WISH
        </h1>

        <p v-if="!candleBlown">
          close your eyes,
          make a little wish...
        </p>

        <p
          v-else
          class="wish-done-text"
        >
          hope it comes true ♡
        </p>

      </div>


      <!-- CUPCAKE -->

      <div
        class="cupcake-area"
        :class="{ 'wish-complete': candleBlown }"
      >

        <!-- SMOKE -->

        <div
          v-if="candleBlown"
          class="smoke-container"
        >

          <span class="smoke smoke-one">
            ~
          </span>

          <span class="smoke smoke-two">
            ~
          </span>

          <span class="smoke smoke-three">
            ~
          </span>

        </div>


        <!-- FLAME -->

        <button
          v-if="!candleBlown"
          class="flame-button"
          aria-label="Blow candle"
          @click="blowCandle"
        >

          <span class="flame">

            <span class="flame-inner"></span>

          </span>

        </button>


        <!-- CANDLE -->

        <div
          class="candle"
          @click="blowCandle"
        >

          <div class="candle-stripe"></div>

          <div class="wick"></div>

        </div>


        <!-- FROSTING -->

        <div
          class="frosting"
          @click="blowCandle"
        >

          <div class="frosting-top"></div>

          <div class="frosting-middle"></div>

          <div class="frosting-bottom"></div>

          <span class="sprinkle sprinkle-1"></span>
          <span class="sprinkle sprinkle-2"></span>
          <span class="sprinkle sprinkle-3"></span>
          <span class="sprinkle sprinkle-4"></span>
          <span class="sprinkle sprinkle-5"></span>
          <span class="sprinkle sprinkle-6"></span>

        </div>


        <!-- CUP -->

        <div class="cupcake-cup">

          <div class="cup-line line-1"></div>
          <div class="cup-line line-2"></div>
          <div class="cup-line line-3"></div>
          <div class="cup-line line-4"></div>

        </div>

      </div>


      <!-- INSTRUCTION -->

      <div
        v-if="!candleBlown"
        class="instruction"
      >

        <span class="arrow">
          ↑
        </span>

        <p>
          tap the flame!
        </p>

      </div>


      <!-- RESULT -->

      <Transition name="result">

        <div
          v-if="candleBlown"
          class="wish-result"
        >

          <span>
            ✦ ✦ ✦
          </span>

          <h2>
            WISH RECEIVED!
          </h2>

          <p>
            whatever you wished for,
            <br>
            I hope you get it ♡
          </p>

          <button
            class="next-button"
            @click="nextPage"
          >
            NEXT →
          </button>

        </div>

      </Transition>


      <!-- PAGE NUMBER -->

      <span class="page-number">
        02
      </span>

    </div>

  </section>
</template>


<style scoped>

/* ================================= */
/* PAGE */
/* ================================= */

.wish-page {
  width: 100%;
  min-height: 100vh;

  display: flex;

  justify-content: center;
  align-items: center;

  padding: 30px;

  position: relative;

  overflow: hidden;

  background-color: #dfcbbb;

  background-image:
    linear-gradient(
      rgba(120, 80, 60, .1) 1px,
      transparent 1px
    ),
    linear-gradient(
      90deg,
      rgba(120, 80, 60, .1) 1px,
      transparent 1px
    );

  background-size:
    35px 35px;
}


/* ================================= */
/* CARD */
/* ================================= */

.wish-card {
  width: min(850px, 95%);

  min-height: 650px;

  position: relative;

  display: flex;

  flex-direction: column;

  justify-content: center;
  align-items: center;

  padding:
    50px 30px;

  background:
    #111;

  border:
    8px solid white;

  box-shadow:
    12px 12px 0
    rgba(0,0,0,.25);

  overflow: hidden;
}


/* ================================= */
/* HEADER */
/* ================================= */

.wish-header {
  text-align: center;

  color: white;

  position: relative;

  z-index: 5;
}


.small-title {
  font-family:
    "Courier New",
    monospace;

  letter-spacing:
    4px;

  font-size:
    13px;

  color:
    #bbb;
}


.wish-header h1 {
  margin:
    15px 0 10px;

  padding:
    5px 15px;

  display:
    inline-block;

  background:
    white;

  color:
    #111;

  font-family:
    Impact,
    sans-serif;

  font-size:
    clamp(38px, 6vw, 65px);

  letter-spacing:
    6px;

  transform:
    rotate(-2deg);

  box-shadow:
    7px 7px 0 #666;
}


.wish-header p {
  font-family:
    "Courier New",
    monospace;

  font-size:
    14px;

  letter-spacing:
    1px;

  color:
    #ddd;

  margin-top:
    25px;
}


.wish-done-text {
  color:
    white !important;

  font-weight:
    bold;
}


/* ================================= */
/* CUPCAKE */
/* ================================= */

.cupcake-area {
  width:
    230px;

  height:
    300px;

  position:
    relative;

  margin-top:
    20px;

  cursor:
    pointer;

  transition:
    .5s ease;
}


.wish-complete {
  transform:
    scale(.92);
}


/* ================================= */
/* FLAME */
/* ================================= */

.flame-button {
  position:
    absolute;

  top:
    0;

  left:
    50%;

  transform:
    translateX(-50%);

  width:
    60px;

  height:
    75px;

  border:
    none;

  background:
    transparent;

  cursor:
    pointer;

  z-index:
    10;
}


.flame {
  width:
    30px;

  height:
    45px;

  position:
    absolute;

  left:
    15px;

  top:
    5px;

  background:
    #f4d46b;

  border-radius:
    50% 50% 50% 50% / 65% 65% 35% 35%;

  transform:
    rotate(45deg);

  animation:
    flameMove
    .6s ease-in-out
    infinite alternate;

  box-shadow:
    0 0 15px
    rgba(255,230,120,.8),
    0 0 35px
    rgba(255,210,80,.4);
}


.flame-inner {
  width:
    13px;

  height:
    22px;

  position:
    absolute;

  right:
    5px;

  bottom:
    5px;

  background:
    white;

  border-radius:
    50%;

  opacity:
    .8;
}


/* ================================= */
/* CANDLE */
/* ================================= */

.candle {
  position:
    absolute;

  width:
    26px;

  height:
    80px;

  left:
    50%;

  top:
    60px;

  transform:
    translateX(-50%);

  z-index:
    5;

  overflow:
    hidden;

  background:
    #eee;

  border:
    3px solid white;
}


.candle-stripe {
  width:
    60px;

  height:
    12px;

  position:
    absolute;

  left:
    -15px;

  top:
    25px;

  background:
    #777;

  transform:
    rotate(-40deg);

  box-shadow:
    0 25px 0 #777;
}


.wick {
  width:
    3px;

  height:
    10px;

  position:
    absolute;

  top:
    -9px;

  left:
    50%;

  background:
    white;
}


/* ================================= */
/* FROSTING */
/* ================================= */

.frosting {
  width:
    200px;

  height:
    120px;

  position:
    absolute;

  left:
    15px;

  top:
    120px;

  z-index:
    4;
}


.frosting-top {
  width:
    90px;

  height:
    70px;

  position:
    absolute;

  top:
    0;

  left:
    55px;

  background:
    #f1ede6;

  border-radius:
    50%;
}


.frosting-middle {
  width:
    145px;

  height:
    70px;

  position:
    absolute;

  top:
    30px;

  left:
    28px;

  background:
    #e7e1d8;

  border-radius:
    50%;
}


.frosting-bottom {
  width:
    190px;

  height:
    65px;

  position:
    absolute;

  bottom:
    0;

  left:
    5px;

  background:
    #d9d1c7;

  border-radius:
    50%;
}


/* ================================= */
/* SPRINKLES */
/* ================================= */

.sprinkle {
  width:
    12px;

  height:
    4px;

  position:
    absolute;

  z-index:
    10;

  background:
    #444;
}


.sprinkle-1 {
  left: 50px;
  top: 60px;

  transform:
    rotate(30deg);
}


.sprinkle-2 {
  left: 90px;
  top: 40px;

  transform:
    rotate(-30deg);
}


.sprinkle-3 {
  right: 40px;
  top: 65px;

  transform:
    rotate(20deg);
}


.sprinkle-4 {
  left: 75px;
  bottom: 20px;

  transform:
    rotate(-15deg);
}


.sprinkle-5 {
  right: 65px;
  bottom: 15px;

  transform:
    rotate(40deg);
}


.sprinkle-6 {
  left: 110px;
  top: 75px;

  transform:
    rotate(70deg);
}


/* ================================= */
/* CUP */
/* ================================= */

.cupcake-cup {
  width:
    160px;

  height:
    100px;

  position:
    absolute;

  left:
    35px;

  bottom:
    0;

  overflow:
    hidden;

  background:
    #777;

  clip-path:
    polygon(
      5% 0,
      95% 0,
      80% 100%,
      20% 100%
    );
}


.cup-line {
  width:
    5px;

  height:
    120px;

  position:
    absolute;

  top:
    -10px;

  background:
    rgba(255,255,255,.35);
}


.line-1 {
  left: 30px;

  transform:
    rotate(-7deg);
}


.line-2 {
  left: 65px;

  transform:
    rotate(-2deg);
}


.line-3 {
  right: 60px;

  transform:
    rotate(2deg);
}


.line-4 {
  right: 30px;

  transform:
    rotate(7deg);
}


/* ================================= */
/* INSTRUCTION */
/* ================================= */

.instruction {
  color:
    white;

  text-align:
    center;

  margin-top:
    15px;

  font-family:
    "Courier New",
    monospace;

  animation:
    instructionMove
    1.3s infinite;
}


.instruction .arrow {
  font-size:
    25px;
}


.instruction p {
  margin:
    5px;

  font-size:
    13px;

  font-weight:
    bold;

  text-decoration:
    underline;
}


/* ================================= */
/* SMOKE */
/* ================================= */

.smoke-container {
  position:
    absolute;

  top:
    5px;

  left:
    50%;

  z-index:
    20;
}


.smoke {
  position:
    absolute;

  color:
    #aaa;

  font-family:
    Georgia,
    serif;

  font-size:
    35px;

  opacity:
    0;

  animation:
    smokeUp
    2.5s ease-out
    infinite;
}


.smoke-one {
  animation-delay:
    0s;
}


.smoke-two {
  animation-delay:
    .6s;
}


.smoke-three {
  animation-delay:
    1.2s;
}


/* ================================= */
/* RESULT */
/* ================================= */

.wish-result {
  margin-top:
    20px;

  text-align:
    center;

  color:
    white;

  position:
    relative;

  z-index:
    30;
}


.wish-result > span {
  letter-spacing:
    15px;

  color:
    #aaa;
}


.wish-result h2 {
  margin:
    10px 0;

  font-family:
    Impact,
    sans-serif;

  font-size:
    30px;

  letter-spacing:
    4px;

  color:
    #fff;
}


.wish-result p {
  font-family:
    "Courier New",
    monospace;

  font-size:
    13px;

  line-height:
    1.6;

  color:
    #ccc;
}


/* ================================= */
/* NEXT */
/* ================================= */

.next-button {
  margin-top:
    20px;

  padding:
    12px 30px;

  background:
    white;

  color:
    #111;

  border:
    3px solid black;

  font-family:
    "Courier New",
    monospace;

  font-weight:
    bold;

  cursor:
    pointer;

  box-shadow:
    6px 6px 0 #777;

  transition:
    .2s;
}


.next-button:hover {
  transform:
    translateY(-4px);

  box-shadow:
    6px 10px 0 #777;
}


/* ================================= */
/* DECORATIONS */
/* ================================= */

.corner-star {
  position:
    absolute;

  color:
    white;

  opacity:
    .5;
}


.star-one {
  top:
    40px;

  left:
    50px;

  font-size:
    60px;

  transform:
    rotate(-15deg);
}


.star-two {
  right:
    60px;

  bottom:
    100px;

  font-size:
    45px;
}


.corner-heart {
  position:
    absolute;

  right:
    40px;

  top:
    100px;

  color:
    white;

  opacity:
    .4;

  font-size:
    70px;

  transform:
    rotate(15deg);
}


.page-number {
  position:
    absolute;

  left:
    35px;

  bottom:
    25px;

  color:
    white;

  opacity:
    .2;

  font-family:
    Impact,
    sans-serif;

  font-size:
    55px;
}


/* ================================= */
/* CONFETTI */
/* ================================= */

.confetti-container {
  position:
    fixed;

  inset:
    0;

  z-index:
    50;

  overflow:
    hidden;

  pointer-events:
    none;
}


.confetti {
  width:
    10px;

  height:
    18px;

  position:
    absolute;

  top:
    -30px;

  animation:
    confettiFall
    linear
    infinite;
}


.confetti-0 {
  background:
    #fff;
}


.confetti-1 {
  background:
    #999;
}


.confetti-2 {
  width:
    8px;

  height:
    8px;

  border:
    2px solid white;

  background:
    transparent;

  border-radius:
    50%;
}


.confetti-3 {
  width:
    15px;

  height:
    4px;

  background:
    #ddd;
}


/* ================================= */
/* TRANSITION */
/* ================================= */

.result-enter-active {
  transition:
    .8s ease;
}


.result-enter-from {
  opacity:
    0;

  transform:
    translateY(30px)
    scale(.8);
}


/* ================================= */
/* ANIMATIONS */
/* ================================= */

@keyframes flameMove {

  from {
    transform:
      rotate(40deg)
      scale(.95);
  }

  to {
    transform:
      rotate(50deg)
      scale(1.08);
  }

}


@keyframes instructionMove {

  0%,
  100% {
    transform:
      translateY(0);
  }

  50% {
    transform:
      translateY(-7px);
  }

}


@keyframes smokeUp {

  0% {
    opacity:
      0;

    transform:
      translate(
        -50%,
        0
      )
      scale(.6);
  }

  25% {
    opacity:
      .8;
  }

  100% {
    opacity:
      0;

    transform:
      translate(
        -30%,
        -100px
      )
      scale(1.5);
  }

}


@keyframes confettiFall {

  0% {
    transform:
      translateY(-10vh)
      rotate(0deg);

    opacity:
      1;
  }

  100% {
    transform:
      translateY(110vh)
      rotate(720deg);

    opacity:
      .3;
  }

}


/* ================================= */
/* MOBILE */
/* ================================= */

@media
(max-width: 600px) {

  .wish-page {
    padding:
      15px;
  }


  .wish-card {
    width:
      100%;

    min-height:
      700px;

    padding:
      45px 20px;
  }


  .wish-header h1 {
    font-size:
      40px;

    letter-spacing:
      4px;
  }


  .small-title {
    font-size:
      10px;

    letter-spacing:
      2px;
  }


  .corner-heart {
    display:
      none;
  }


  .star-one {
    left:
      20px;

    font-size:
      35px;
  }


  .star-two {
    right:
      20px;

    font-size:
      30px;
  }

}
</style>