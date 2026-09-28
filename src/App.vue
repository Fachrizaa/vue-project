<script setup>
import { ref, nextTick } from 'vue'

import OpeningPage from './components/OpeningPage.vue'
import QuestionPage from './components/QuestionPage.vue'
import MysteryBox from './components/MysteryBox.vue'
import PhotoRecap from './components/PhotoRecap.vue'
import MakeAWish from './components/MakeAWish.vue'
import BirthdayFinale from './components/BirthdayFinale.vue'

import birthdayMusic from './assets/music/birthday.mp3'

const currentPage = ref(1)

const audioPlayer = ref(null)
const musicStarted = ref(false)
const isMuted = ref(false)

/* =========================
   START MUSIC
========================= */

const startMusic = async () => {
  if (musicStarted.value) return

  try {
    await audioPlayer.value?.play()
    musicStarted.value = true
  } catch (error) {
    console.log('Audio belum bisa diputar:', error)
  }
}


/* =========================
   NEXT PAGE
========================= */

const nextPage = async () => {

  /*
    Jika NEXT pertama ditekan,
    musik langsung dimulai.
  */

  if (currentPage.value === 1) {
    await startMusic()
  }

  currentPage.value++

  await nextTick()

  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
}


/* =========================
   MUTE / UNMUTE
========================= */

const toggleMusic = () => {

  if (!audioPlayer.value) return

  isMuted.value = !isMuted.value

  audioPlayer.value.muted = isMuted.value
}


/* =========================
   REPLAY
========================= */

const replayWebsite = async () => {

  currentPage.value = 1

  /*
    Musik juga mulai dari awal lagi.
  */

  if (audioPlayer.value) {
    audioPlayer.value.currentTime = 0

    if (musicStarted.value) {
      await audioPlayer.value.play()
    }
  }

  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
}
</script>

<template>

  <main>

    <!-- BACKGROUND MUSIC -->

    <audio ref="audioPlayer" :src="birthdayMusic" loop preload="auto"></audio>


    <!-- MUSIC CONTROL -->

    <button v-if="musicStarted" class="music-control" @click="toggleMusic"
      :title="isMuted ? 'Turn music on' : 'Turn music off'">

      {{ isMuted ? '🔇' : '♫' }}

    </button>


    <!-- PAGE 1 -->

    <OpeningPage v-if="currentPage === 1" @next="nextPage" />


    <!-- PAGE 2 -->

    <QuestionPage v-else-if="currentPage === 2" @next="nextPage" />


    <!-- PAGE 3 -->

    <MysteryBox v-else-if="currentPage === 3" @next="nextPage" />


    <!-- PAGE 4 -->

    <PhotoRecap v-else-if="currentPage === 4" @next="nextPage" />


    <!-- PAGE 5 -->

    <MakeAWish v-else-if="currentPage === 5" @next="nextPage" />


    <!-- PAGE 6 -->

    <BirthdayFinale v-else-if="currentPage === 6" @replay="replayWebsite" />

  </main>

</template>


<style>
* {
  box-sizing: border-box;
}

.music-control {
  position: fixed;

  top: 20px;
  left: 20px;

  z-index: 9999;

  width: 45px;
  height: 45px;

  display: flex;
  justify-content: center;
  align-items: center;

  border: 3px solid #111;

  background: white;
  color: #111;

  font-size: 20px;

  cursor: pointer;

  box-shadow:
    5px 5px 0 rgba(0, 0, 0, .4);

  transition: .2s;
}


.music-control:hover {
  transform:
    translateY(-3px);

  box-shadow:
    5px 8px 0 rgba(0, 0, 0, .4);
}


.music-control:active {
  transform:
    translate(3px, 3px);

  box-shadow:
    2px 2px 0 rgba(0, 0, 0, .4);
}


@media (max-width: 600px) {

  .music-control {
    top: 15px;
    left: 15px;

    width: 40px;
    height: 40px;

    font-size: 17px;
  }

}

html,
body,
#app {
  width: 100%;
  min-height: 100%;

  margin: 0;
  padding: 0;
}

html {
  scroll-behavior: smooth;
}

body {
  margin: 0;

  overflow-x: hidden;

  background: #111;
}

button {
  -webkit-tap-highlight-color: transparent;
}
</style>
