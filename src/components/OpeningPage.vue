<script setup>
defineEmits(['next'])
</script>

<template>
  <section class="opening-page">

    <!-- Dekorasi -->
    <div class="spark spark-1">✦</div>
    <div class="spark spark-2">✦</div>
    <div class="spark spark-3">★</div>

    <div class="birthday-card">

      <div class="birthday-text">
        <span class="small-text">HAPPY</span>

        <h1>
          <span>B</span>
          <span>I</span>
          <span>R</span>
          <span>T</span>
          <span>H</span>
          <span>D</span>
          <span>A</span>
          <span>Y</span>
        </h1>

        <h2>MY LOVE!</h2>

        <p>
          A little surprise<br />
          made especially for you.
        </p>
      </div>

      <div class="cake">
        <div class="candles">
          <span>🔥</span>
          <span>🔥</span>
          <span>🔥</span>
        </div>

        <div class="cake-top"></div>
        <div class="cake-body">
          <span>♡</span>
          <span>♡</span>
          <span>♡</span>
        </div>
      </div>

      <button
        class="next-button"
        @click="$emit('next')"
      >
        NEXT ➜
      </button>

    </div>

    <div class="bottom-text">
      ✦ a birthday story ✦
    </div>

  </section>
</template>

<style scoped>
.opening-page {
  width: 100%;
  min-height: 100vh;

  display: flex;
  justify-content: center;
  align-items: center;

  position: relative;
  overflow: hidden;

  padding: 30px;

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

/* CARD */

.birthday-card {
  width: min(850px, 95%);

  min-height: 500px;

  background:
    linear-gradient(
      rgba(0,0,0,0.55),
      rgba(0,0,0,0.75)
    ),
    #151515;

  border: 8px solid white;

  box-shadow:
    10px 10px 0 rgba(0,0,0,0.25);

  position: relative;

  display: flex;
  justify-content: center;
  align-items: center;

  text-align: center;

  transform: rotate(-1deg);
}

/* TEXT */

.birthday-text {
  color: white;
}

.small-text {
  letter-spacing: 12px;
  font-size: 25px;
  font-weight: bold;
}

h1 {
  margin: 10px 0;

  display: flex;
  justify-content: center;
  flex-wrap: wrap;

  gap: 5px;
}

h1 span {
  font-size: clamp(35px, 7vw, 75px);

  background: white;
  color: black;

  padding: 5px 9px;

  font-family: Impact, sans-serif;

  transform: rotate(-3deg);

  box-shadow: 4px 4px 0 #777;
}

h1 span:nth-child(even) {
  background: #d46a6a;
  color: white;

  transform: rotate(3deg);
}

h2 {
  font-size: clamp(40px, 8vw, 85px);

  color: white;

  margin: 0;

  font-family: Georgia, serif;

  letter-spacing: 8px;

  text-transform: lowercase;
}

p {
  margin-top: 20px;

  font-family: "Courier New", monospace;

  font-size: 17px;

  line-height: 1.6;

  color: #ddd;
}

/* BUTTON */

.next-button {
  position: absolute;

  top: 30px;
  right: 30px;

  background: white;
  color: black;

  border: none;

  padding: 14px 25px;

  font-family: "Courier New", monospace;

  font-size: 17px;
  font-weight: bold;

  cursor: pointer;

  box-shadow: 5px 5px 0 #888;

  transition: 0.2s;
}

.next-button:hover {
  transform: translateY(-4px);

  box-shadow:
    5px 9px 0 #888;
}

/* CAKE */

.cake {
  position: absolute;

  left: 50px;
  bottom: 35px;

  width: 120px;
}

.candles {
  display: flex;
  justify-content: space-around;

  font-size: 20px;
}

.cake-top {
  height: 20px;

  background: #f4e0d0;

  border-radius: 50%;
}

.cake-body {
  height: 70px;

  background: #8b5e4c;

  display: flex;
  align-items: center;
  justify-content: space-around;

  font-size: 20px;
  color: white;
}

/* DECORATION */

.spark {
  position: absolute;

  font-size: 40px;

  color: #755a4a;

  animation: float 3s ease-in-out infinite;
}

.spark-1 {
  top: 10%;
  left: 8%;
}

.spark-2 {
  bottom: 15%;
  right: 8%;
}

.spark-3 {
  top: 15%;
  right: 12%;
}

.bottom-text {
  position: absolute;

  bottom: 15px;

  font-family: "Courier New", monospace;

  font-weight: bold;

  color: #725747;
}

/* ANIMATION */

@keyframes float {

  0%,
  100% {
    transform: translateY(0) rotate(0);
  }

  50% {
    transform: translateY(-12px) rotate(10deg);
  }
}

/* MOBILE */

@media (max-width: 600px) {

  .opening-page {
    padding: 18px;
  }

  .birthday-card {
    min-height: 600px;
  }

  .small-text {
    font-size: 17px;
    letter-spacing: 7px;
  }

  h1 span {
    font-size: 30px;
    padding: 4px 6px;
  }

  h2 {
    font-size: 45px;
  }

  p {
    font-size: 14px;
  }

  .cake {
    width: 80px;

    left: 25px;
    bottom: 25px;
  }

  .next-button {
    top: 20px;
    right: 20px;

    font-size: 14px;

    padding: 10px 16px;
  }
}
</style>