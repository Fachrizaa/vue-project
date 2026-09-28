<script setup>
import { ref } from 'vue'

const emit = defineEmits(['replay'])

const birthdayGirl = ref('INDI FITRIA RAMADHANI')

const confetti = Array.from({ length: 70 }, (_, i) => ({
    id: i,
    left: Math.random() * 100,
    delay: Math.random() * 4,
    duration: 4 + Math.random() * 3,
    type: i % 4
}))

const replay = () => {
    emit('replay')
}
</script>

<template>
    <section class="finale-page">

        <!-- CONFETTI -->
        <div class="confetti-container">
            <span v-for="item in confetti" :key="item.id" class="confetti" :class="`confetti-${item.type}`" :style="{
                left: `${item.left}%`,
                animationDelay: `${item.delay}s`,
                animationDuration: `${item.duration}s`
            }" />
        </div>


        <div class="finale-card">

            <!-- DECORATION -->
            <span class="decoration star star-1">✦</span>
            <span class="decoration star star-2">★</span>
            <span class="decoration star star-3">✦</span>

            <span class="decoration heart heart-1">♡</span>
            <span class="decoration heart heart-2">♡</span>


            <!-- SMALL TEXT -->
            <p class="once-again">
                and once again...
            </p>


            <!-- HAPPY -->
            <div class="happy-text">
                HAPPY
            </div>


            <!-- BIRTHDAY -->
            <div class="birthday-text">

                <span>B</span>
                <span>I</span>
                <span>R</span>
                <span>T</span>
                <span>H</span>
                <span>D</span>
                <span>A</span>
                <span>Y</span>

            </div>


            <!-- NAME -->
            <h1 class="girl-name">
                {{ birthdayGirl }}
            </h1>


            <!-- CAKE -->
            <div class="cake-wrapper">

                <!-- CANDLES -->

                <div class="candles">

                    <div class="candle">
                        <span class="flame"></span>
                    </div>

                    <div class="candle">
                        <span class="flame"></span>
                    </div>

                    <div class="candle">
                        <span class="flame"></span>
                    </div>

                    <div class="candle">
                        <span class="flame"></span>
                    </div>

                    <div class="candle">
                        <span class="flame"></span>
                    </div>

                </div>


                <!-- CAKE TOP -->

                <div class="cake-top">

                    <span class="cream cream-1"></span>
                    <span class="cream cream-2"></span>
                    <span class="cream cream-3"></span>

                </div>


                <!-- CAKE MIDDLE -->

                <div class="cake-middle">

                    <span>♡</span>
                    <span>★</span>
                    <span>♡</span>
                    <span>★</span>
                    <span>♡</span>

                </div>


                <!-- CAKE BOTTOM -->

                <div class="cake-bottom">

                    <div class="cake-line"></div>

                </div>


                <!-- PLATE -->

                <div class="plate"></div>

            </div>


            <!-- FINAL MESSAGE -->

            <div class="final-message">

                <span class="quote-mark">
                    “
                </span>

                <p>
                    I hope this year brings you
                    all the happiness you deserve.
                    Keep smiling, keep growing,
                    and keep being the amazing
                    person you are.
                </p>

                <strong>
                    Happy Birthday, {{ birthdayGirl }} ♡
                </strong>

            </div>


            <!-- END -->

            <div class="the-end">

                <span>✦</span>

                THE END

                <span>✦</span>

            </div>


            <!-- REPLAY -->

            <button class="replay-button" @click="replay">
                ↻ REPLAY FROM THE START
            </button>


            <!-- PAGE -->

            <span class="page-number">
                FIN.
            </span>

        </div>

    </section>
</template>


<style scoped>
/* ==========================================
   PAGE
========================================== */

.finale-page {
    width: 100%;
    min-height: 100vh;

    display: flex;
    justify-content: center;
    align-items: center;

    position: relative;

    padding: 30px;

    overflow: hidden;

    background-color: #dfcbbb;

    background-image:
        linear-gradient(rgba(100, 70, 50, .1) 1px,
            transparent 1px),
        linear-gradient(90deg,
            rgba(100, 70, 50, .1) 1px,
            transparent 1px);

    background-size: 35px 35px;
}


/* ==========================================
   MAIN CARD
========================================== */

.finale-card {
    width: min(900px, 95%);

    min-height: 850px;

    position: relative;

    display: flex;
    flex-direction: column;

    justify-content: center;
    align-items: center;

    padding:
        70px 40px;

    overflow: hidden;

    background:
        radial-gradient(circle at center,
            #272727,
            #101010 65%);

    border:
        9px solid white;

    box-shadow:
        14px 14px 0 rgba(0, 0, 0, .25);

    animation:
        cardAppear .8s ease;
}


/* ==========================================
   SMALL TEXT
========================================== */

.once-again {
    margin:
        0 0 20px;

    color:
        #aaa;

    font-family:
        "Courier New",
        monospace;

    font-size:
        13px;

    letter-spacing:
        4px;

    animation:
        fadeDown 1s ease;
}


/* ==========================================
   HAPPY
========================================== */

.happy-text {
    color:
        white;

    font-family:
        Georgia,
        serif;

    font-size:
        clamp(45px, 8vw, 90px);

    font-style:
        italic;

    font-weight:
        bold;

    line-height:
        1;

    transform:
        rotate(-3deg);

    animation:
        titleAppear .9s ease;
}


/* ==========================================
   BIRTHDAY LETTERS
========================================== */

.birthday-text {
    display: flex;

    justify-content: center;

    gap:
        5px;

    margin-top:
        10px;

    flex-wrap:
        wrap;

    position:
        relative;

    z-index:
        5;
}


.birthday-text span {
    display:
        inline-block;

    padding:
        4px 10px;

    background:
        white;

    color:
        #111;

    font-family:
        Impact,
        sans-serif;

    font-size:
        clamp(35px, 6vw, 65px);

    box-shadow:
        4px 5px 0 #666;

    animation:
        letterAppear .6s ease backwards;
}


.birthday-text span:nth-child(1) {
    transform: rotate(-5deg);
    animation-delay: .1s;
}

.birthday-text span:nth-child(2) {
    transform: rotate(3deg);
    animation-delay: .2s;
}

.birthday-text span:nth-child(3) {
    transform: rotate(-2deg);
    animation-delay: .3s;
}

.birthday-text span:nth-child(4) {
    transform: rotate(4deg);
    animation-delay: .4s;
}

.birthday-text span:nth-child(5) {
    transform: rotate(-4deg);
    animation-delay: .5s;
}

.birthday-text span:nth-child(6) {
    transform: rotate(2deg);
    animation-delay: .6s;
}

.birthday-text span:nth-child(7) {
    transform: rotate(-3deg);
    animation-delay: .7s;
}

.birthday-text span:nth-child(8) {
    transform: rotate(4deg);
    animation-delay: .8s;
}


/* ==========================================
   NAME
========================================== */

.girl-name {
    margin:
        25px 0 10px;

    color:
        white;

    text-align:
        center;

    font-family:
        "Courier New",
        monospace;

    font-size:
        clamp(25px, 5vw, 50px);

    letter-spacing:
        7px;

    text-transform:
        uppercase;

    animation:
        nameAppear 1.3s ease;
}


/* ==========================================
   CAKE
========================================== */

.cake-wrapper {
    width:
        310px;

    height:
        300px;

    position:
        relative;

    margin:
        40px auto 20px;

    animation:
        cakeAppear 1s ease;
}


/* CANDLES */

.candles {
    height:
        75px;

    display:
        flex;

    justify-content:
        center;

    align-items:
        flex-end;

    gap:
        22px;
}


.candle {
    width:
        15px;

    height:
        50px;

    position:
        relative;

    background:
        repeating-linear-gradient(-45deg,
            #eee,
            #eee 6px,
            #777 6px,
            #777 10px);

    border:
        2px solid white;
}


.flame {
    width:
        14px;

    height:
        22px;

    position:
        absolute;

    top:
        -28px;

    left:
        -1px;

    background:
        #f0d889;

    border-radius:
        50% 50% 45% 45%;

    transform:
        rotate(45deg);

    box-shadow:
        0 0 15px rgba(255, 220, 130, .8);

    animation:
        flame .6s ease-in-out infinite alternate;
}


/* CAKE TOP */

.cake-top {
    width:
        230px;

    height:
        55px;

    margin:
        auto;

    position:
        relative;

    z-index:
        4;

    background:
        #eee7dd;

    border-radius:
        50%;

    border:
        3px solid #bbb;
}


.cream {
    width:
        35px;

    height:
        35px;

    position:
        absolute;

    bottom:
        -15px;

    background:
        #eee7dd;

    border-radius:
        50%;
}


.cream-1 {
    left:
        25px;
}


.cream-2 {
    left:
        95px;
}


.cream-3 {
    right:
        25px;
}


/* MIDDLE */

.cake-middle {
    width:
        230px;

    height:
        95px;

    margin:
        -25px auto 0;

    padding-top:
        45px;

    display:
        flex;

    justify-content:
        space-around;

    position:
        relative;

    z-index:
        3;

    background:
        #aaa;

    border:
        3px solid #777;

    color:
        white;

    font-size:
        20px;
}


/* BOTTOM */

.cake-bottom {
    width:
        265px;

    height:
        70px;

    margin:
        -5px auto 0;

    position:
        relative;

    background:
        #777;

    border:
        3px solid #555;
}


.cake-line {
    width:
        100%;

    height:
        12px;

    position:
        absolute;

    top:
        25px;

    background:
        #aaa;
}


/* PLATE */

.plate {
    width:
        310px;

    height:
        25px;

    margin:
        -5px auto 0;

    background:
        #ddd;

    border-radius:
        50%;

    border:
        3px solid #999;
}


/* ==========================================
   FINAL MESSAGE
========================================== */

.final-message {
    width:
        min(550px, 90%);

    margin-top:
        30px;

    padding:
        25px 30px;

    position:
        relative;

    background:
        #f4efe5;

    color:
        #222;

    text-align:
        center;

    font-family:
        "Courier New",
        monospace;

    line-height:
        1.7;

    transform:
        rotate(-1deg);

    box-shadow:
        8px 8px 0 #666;
}


.final-message p {
    margin:
        0 0 15px;

    font-size:
        14px;
}


.final-message strong {
    font-size:
        15px;
}


.quote-mark {
    position:
        absolute;

    left:
        10px;

    top:
        -20px;

    color:
        #555;

    font-family:
        Georgia,
        serif;

    font-size:
        70px;
}


/* ==========================================
   THE END
========================================== */

.the-end {
    margin-top:
        40px;

    color:
        white;

    font-family:
        Impact,
        sans-serif;

    font-size:
        30px;

    letter-spacing:
        8px;
}


.the-end span {
    color:
        #777;
}


/* ==========================================
   REPLAY
========================================== */

.replay-button {
    margin-top:
        25px;

    padding:
        12px 25px;

    background:
        white;

    color:
        black;

    border:
        3px solid black;

    font-family:
        "Courier New",
        monospace;

    font-size:
        12px;

    font-weight:
        bold;

    cursor:
        pointer;

    box-shadow:
        6px 6px 0 #666;

    transition:
        .2s;
}


.replay-button:hover {
    transform:
        translateY(-4px);

    box-shadow:
        6px 10px 0 #666;
}


/* ==========================================
   DECORATIONS
========================================== */

.decoration {
    position:
        absolute;

    color:
        white;

    opacity:
        .3;

    pointer-events:
        none;
}


.star-1 {
    left:
        50px;

    top:
        80px;

    font-size:
        60px;

    transform:
        rotate(-15deg);
}


.star-2 {
    right:
        60px;

    top:
        190px;

    font-size:
        35px;
}


.star-3 {
    left:
        70px;

    bottom:
        150px;

    font-size:
        40px;
}


.heart-1 {
    right:
        40px;

    bottom:
        250px;

    font-size:
        70px;

    transform:
        rotate(15deg);
}


.heart-2 {
    left:
        50px;

    top:
        350px;

    font-size:
        50px;

    transform:
        rotate(-15deg);
}


.page-number {
    position:
        absolute;

    right:
        30px;

    bottom:
        20px;

    color:
        white;

    opacity:
        .15;

    font-family:
        Impact,
        sans-serif;

    font-size:
        45px;
}


/* ==========================================
   CONFETTI
========================================== */

.confetti-container {
    position:
        fixed;

    inset:
        0;

    overflow:
        hidden;

    pointer-events:
        none;

    z-index:
        50;
}


.confetti {
    width:
        9px;

    height:
        18px;

    position:
        absolute;

    top:
        -30px;

    animation:
        confettiFall linear infinite;
}


.confetti-0 {
    background:
        white;
}


.confetti-1 {
    background:
        #888;
}


.confetti-2 {
    width:
        9px;

    height:
        9px;

    background:
        transparent;

    border:
        2px solid white;

    border-radius:
        50%;
}


.confetti-3 {
    width:
        15px;

    height:
        4px;

    background:
        #ccc;
}


/* ==========================================
   ANIMATIONS
========================================== */

@keyframes cardAppear {

    from {
        opacity:
            0;

        transform:
            scale(.92);
    }

    to {
        opacity:
            1;

        transform:
            scale(1);
    }

}


@keyframes fadeDown {

    from {
        opacity:
            0;

        transform:
            translateY(-20px);
    }

}


@keyframes titleAppear {

    from {
        opacity:
            0;

        transform:
            translateY(-30px) rotate(-8deg);
    }

}


@keyframes letterAppear {

    from {
        opacity:
            0;

        transform:
            scale(.3) rotate(20deg);
    }

}


@keyframes nameAppear {

    from {
        opacity:
            0;

        letter-spacing:
            20px;
    }

}


@keyframes cakeAppear {

    from {
        opacity:
            0;

        transform:
            translateY(70px) scale(.8);
    }

}


@keyframes flame {

    from {
        transform:
            rotate(40deg) scale(.9);
    }

    to {
        transform:
            rotate(50deg) scale(1.1);
    }

}


@keyframes confettiFall {

    from {
        transform:
            translateY(-10vh) rotate(0deg);

        opacity:
            1;
    }

    to {
        transform:
            translateY(110vh) rotate(720deg);

        opacity:
            .2;
    }

}


/* ==========================================
   MOBILE
========================================== */

@media (max-width: 600px) {

    .finale-page {
        padding:
            15px;
    }


    .finale-card {
        width:
            100%;

        min-height:
            900px;

        padding:
            60px 20px;
    }


    .birthday-text {
        gap:
            3px;
    }


    .birthday-text span {
        padding:
            4px 6px;

        font-size:
            30px;
    }


    .girl-name {
        font-size:
            25px;

        letter-spacing:
            4px;
    }


    .cake-wrapper {
        transform:
            scale(.85);

        margin:
            20px auto 0;
    }


    .final-message {
        padding:
            25px 20px;
    }


    .final-message p {
        font-size:
            12px;
    }


    .decoration {
        opacity:
            .15;
    }


    .star-1 {
        left:
            20px;
    }


    .star-2 {
        right:
            20px;
    }


    .heart-1,
    .heart-2 {
        display:
            none;
    }


    .the-end {
        font-size:
            22px;

        letter-spacing:
            5px;
    }

}
</style>