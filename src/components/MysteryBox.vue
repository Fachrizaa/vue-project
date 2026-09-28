<script setup>
import { ref } from 'vue'

const emit = defineEmits(['next'])

const step = ref('box')

const openBox = () => {
  step.value = 'opening'

  setTimeout(() => {
    step.value = 'paper'
  }, 900)
}

const openLetter = () => {
  step.value = 'letter'
}

const nextPage = () => {
  emit('next')
}
</script>

<template>
  <section class="mystery-page">

    <div class="manga-card">

      <!-- ================================= -->
      <!-- STEP 1 : CLOSED BOX -->
      <!-- ================================= -->

      <div
        v-if="step === 'box'"
        class="scene box-scene"
      >

        <div class="speech speech-top">
          OPEN IT DUMBO!
        </div>

        <div
          class="gift-box"
          @click="openBox"
        >

          <div class="box-lid"></div>

          <div class="box-body">
            <span>?</span>
          </div>

        </div>

        <div class="bang">
          BANG!!
        </div>

        <button
          class="action-button"
          @click="openBox"
        >
          OPEN
        </button>

      </div>


      <!-- ================================= -->
      <!-- STEP 2 : OPENING -->
      <!-- ================================= -->

      <div
        v-else-if="step === 'opening'"
        class="scene opening-scene"
      >

        <div class="opening-box">

          <div class="open-lid"></div>

          <div class="paper-ball">
            📄
          </div>

          <div class="box-body open-body"></div>

        </div>

        <div class="flash">
          ✦
        </div>

      </div>


      <!-- ================================= -->
      <!-- STEP 3 : PAPER -->
      <!-- ================================= -->

      <div
        v-else-if="step === 'paper'"
        class="scene paper-scene"
      >

        <div class="speech paper-text">
          Huh? What's this?
        </div>

        <div
          class="crumpled-paper"
          @click="openLetter"
        >

          <span>📄</span>

        </div>

        <button
          class="action-button uncrumple"
          @click="openLetter"
        >
          UNCRUMPLE THE PAPER
        </button>

      </div>


      <!-- ================================= -->
      <!-- STEP 4 : LETTER -->
      <!-- ================================= -->

      <div
        v-else-if="step === 'letter'"
        class="scene letter-scene"
      >

        <div class="letter-wrapper">

          <div class="tape tape-left"></div>
          <div class="tape tape-right"></div>

          <article class="birthday-letter">

            <div class="letter-header">
              My Love,
            </div>

            <p>
              Happy birthday to one of the most
              special people in my life.
            </p>

            <p>
              I hope this new chapter brings you
              more happiness, more unforgettable
              memories, and everything you've
              been wishing for.
            </p>

            <p>
              Thank you for all the random talks,
              stupid jokes, laughs, and moments
              we've shared together.
            </p>

            <p>
              No matter how annoying you are,
              I'm still grateful that somehow
              our paths crossed.
            </p>

            <p>
              Keep being you, keep chasing
              everything you want, and please
              don't forget to enjoy the little
              things along the way.
            </p>

            <div class="letter-ending">
              Happy Birthday, My Love ♡
            </div>

          </article>

          <div class="cat-sticker">
            ฅ^•ﻌ•^ฅ
          </div>

          <div class="heart-sticker">
            ♡
          </div>

        </div>

        <button
          class="next-button"
          @click="nextPage"
        >
          NEXT →
        </button>

      </div>

    </div>

  </section>
</template>

<style scoped>

/* ================================= */
/* BACKGROUND */
/* ================================= */

.mystery-page {
  width: 100%;
  min-height: 100vh;

  display: flex;
  justify-content: center;
  align-items: center;

  padding: 30px;

  overflow: hidden;

  background-color: #e4d1c0;

  background-image:
    linear-gradient(
      90deg,
      rgba(120, 80, 60, 0.12) 50%,
      transparent 50%
    ),
    linear-gradient(
      rgba(120, 80, 60, 0.12) 50%,
      transparent 50%
    );

  background-size: 80px 80px;
}


/* ================================= */
/* MAIN CARD */
/* ================================= */

.manga-card {
  width: min(900px, 95%);
  min-height: 570px;

  position: relative;

  overflow: hidden;

  border: 8px solid white;

  background-color: #d4d4d4;

  background-image:
    linear-gradient(
      45deg,
      rgba(0,0,0,.08) 25%,
      transparent 25%
    ),
    linear-gradient(
      -45deg,
      rgba(0,0,0,.08) 25%,
      transparent 25%
    ),
    linear-gradient(
      45deg,
      transparent 75%,
      rgba(0,0,0,.08) 75%
    ),
    linear-gradient(
      -45deg,
      transparent 75%,
      rgba(0,0,0,.08) 75%
    );

  background-size: 40px 40px;

  box-shadow:
    12px 12px 0 rgba(0,0,0,.25);
}


/* ================================= */
/* SCENE */
/* ================================= */

.scene {
  min-height: 570px;

  display: flex;

  flex-direction: column;

  justify-content: center;
  align-items: center;

  position: relative;

  animation:
    sceneEnter .5s ease;
}


/* ================================= */
/* SPEECH */
/* ================================= */

.speech {
  background: white;

  border: 4px solid black;

  padding: 12px 30px;

  font-family:
    "Courier New",
    monospace;

  font-weight: bold;

  box-shadow:
    7px 7px 0 #555;
}


.speech-top {
  position: absolute;

  top: 45px;

  font-size: 21px;

  transform:
    rotate(-2deg);
}


/* ================================= */
/* BOX */
/* ================================= */

.gift-box {
  position: relative;

  width: 260px;

  height: 210px;

  cursor: pointer;

  transition: .25s;

  margin-top: 50px;
}


.gift-box:hover {
  transform:
    scale(1.05)
    rotate(-2deg);
}


.box-lid {
  width: 280px;
  height: 55px;

  position: absolute;

  left: -10px;
  top: 0;

  z-index: 3;

  background:
    linear-gradient(
      135deg,
      #292929,
      #050505
    );

  border: 4px solid #000;

  box-shadow:
    7px 8px 0 rgba(0,0,0,.25);
}


.box-body {
  position: absolute;

  width: 250px;
  height: 160px;

  left: 5px;
  bottom: 0;

  background:
    linear-gradient(
      135deg,
      #252525,
      #050505
    );

  border: 4px solid black;

  display: flex;

  justify-content: center;
  align-items: center;

  box-shadow:
    8px 10px 0 rgba(0,0,0,.3);
}


.box-body span {
  color: white;

  font-family:
    Georgia,
    serif;

  font-size: 70px;

  opacity: .15;
}


/* ================================= */
/* BANG */
/* ================================= */

.bang {
  position: absolute;

  right: 90px;
  bottom: 150px;

  font-family:
    Impact,
    sans-serif;

  font-size: 25px;

  transform:
    rotate(12deg);
}


/* ================================= */
/* BUTTON */
/* ================================= */

.action-button {
  margin-top: 30px;

  background: white;

  border: 4px solid black;

  padding: 13px 35px;

  font-family:
    "Courier New",
    monospace;

  font-weight: bold;

  font-size: 18px;

  cursor: pointer;

  box-shadow:
    7px 7px 0 #555;

  transition: .2s;
}


.action-button:hover {
  transform:
    translateY(-5px);

  box-shadow:
    7px 12px 0 #555;
}


.action-button:active {
  transform:
    translate(5px,5px);

  box-shadow: none;
}


/* ================================= */
/* OPENING ANIMATION */
/* ================================= */

.opening-box {
  position: relative;

  width: 300px;
  height: 300px;
}


.open-body {
  bottom: 0;
}


.open-lid {
  width: 280px;
  height: 55px;

  position: absolute;

  top: 20px;
  left: 10px;

  z-index: 5;

  background: #111;

  border: 4px solid black;

  animation:
    lidOpen
    .9s ease
    forwards;
}


.paper-ball {
  position: absolute;

  z-index: 4;

  left: 110px;
  bottom: 80px;

  font-size: 70px;

  animation:
    paperJump
    .9s ease
    forwards;
}


.flash {
  position: absolute;

  font-size: 100px;

  animation:
    flashAnimation
    .7s infinite;
}


/* ================================= */
/* CRUMPLED PAPER */
/* ================================= */

.paper-scene {
  background:
    rgba(255,255,255,.15);
}


.paper-text {
  margin-bottom: 40px;

  transform:
    rotate(2deg);
}


.crumpled-paper {
  width: 170px;
  height: 150px;

  display: flex;

  justify-content: center;
  align-items: center;

  cursor: pointer;

  background:
    #e9e4d7;

  border-radius:
    48% 52% 60% 40%;

  box-shadow:
    10px 12px 0
    rgba(0,0,0,.25);

  transform:
    rotate(-7deg);

  transition:
    .25s;
}


.crumpled-paper span {
  font-size: 80px;
}


.crumpled-paper:hover {
  transform:
    rotate(4deg)
    scale(1.08);
}


.uncrumple {
  font-size: 14px;
}


/* ================================= */
/* LETTER */
/* ================================= */

.letter-scene {
  padding:
    40px 20px;
}


.letter-wrapper {
  width:
    min(600px, 90%);

  position:
    relative;
}


.birthday-letter {
  background:
    #f7f0df;

  padding:
    50px 55px;

  color:
    #27231f;

  border:
    1px solid #c7bca5;

  box-shadow:
    10px 12px 0
    rgba(0,0,0,.2);

  transform:
    rotate(-1deg);

  font-family:
    Georgia,
    serif;

  line-height:
    1.8;

  animation:
    unfoldLetter
    .8s ease;
}


.letter-header {
  font-size: 30px;

  font-weight: bold;

  margin-bottom: 25px;
}


.birthday-letter p {
  font-size: 16px;

  margin:
    15px 0;
}


.letter-ending {
  margin-top:
    30px;

  font-size:
    22px;

  font-weight:
    bold;

  text-align:
    right;
}


/* ================================= */
/* TAPE */
/* ================================= */

.tape {
  width: 100px;
  height: 30px;

  background:
    rgba(210,190,150,.7);

  position:
    absolute;

  z-index: 5;
}


.tape-left {
  top: -8px;
  left: -25px;

  transform:
    rotate(-35deg);
}


.tape-right {
  top: -8px;
  right: -25px;

  transform:
    rotate(35deg);
}


/* ================================= */
/* STICKERS */
/* ================================= */

.cat-sticker {
  position:
    absolute;

  bottom:
    -15px;

  left:
    -30px;

  font-size:
    45px;

  transform:
    rotate(-10deg);
}


.heart-sticker {
  position:
    absolute;

  right:
    -20px;

  top:
    100px;

  font-size:
    60px;

  transform:
    rotate(15deg);
}


/* ================================= */
/* NEXT */
/* ================================= */

.next-button {
  margin-top:
    35px;

  background:
    #111;

  color:
    white;

  border:
    4px solid white;

  padding:
    13px 35px;

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
}


/* ================================= */
/* ANIMATIONS */
/* ================================= */

@keyframes sceneEnter {

  from {
    opacity: 0;

    transform:
      scale(.95);
  }

  to {
    opacity: 1;

    transform:
      scale(1);
  }

}


@keyframes lidOpen {

  0% {
    transform:
      translateY(100px)
      rotate(0);
  }

  100% {
    transform:
      translateY(-70px)
      translateX(-70px)
      rotate(-25deg);
  }

}


@keyframes paperJump {

  0% {
    transform:
      translateY(0)
      rotate(0);
  }

  60% {
    transform:
      translateY(-120px)
      rotate(15deg);
  }

  100% {
    transform:
      translateY(-70px)
      rotate(-8deg);
  }

}


@keyframes flashAnimation {

  0%,
  100% {
    opacity: .2;

    transform:
      scale(.8);
  }

  50% {
    opacity: 1;

    transform:
      scale(1.2);
  }

}


@keyframes unfoldLetter {

  from {
    opacity: 0;

    transform:
      scale(.4)
      rotate(-15deg);
  }

  to {
    opacity: 1;

    transform:
      scale(1)
      rotate(-1deg);
  }

}


/* ================================= */
/* MOBILE */
/* ================================= */

@media
(max-width: 600px) {

  .mystery-page {
    padding: 15px;
  }


  .manga-card {
    min-height: 650px;
  }


  .scene {
    min-height: 650px;
  }


  .speech-top {
    font-size: 16px;

    top: 50px;
  }


  .gift-box {
    transform:
      scale(.8);
  }


  .gift-box:hover {
    transform:
      scale(.85);
  }


  .bang {
    right: 25px;

    bottom: 180px;

    font-size: 18px;
  }


  .birthday-letter {
    padding:
      40px 30px;
  }


  .letter-header {
    font-size:
      25px;
  }


  .birthday-letter p {
    font-size:
      14px;

    line-height:
      1.6;
  }


  .letter-ending {
    font-size:
      18px;
  }


  .cat-sticker {
    font-size:
      30px;
  }


  .heart-sticker {
    font-size:
      40px;
  }

}

</style>