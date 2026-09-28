<script setup>
import { computed, ref } from 'vue'

import photo1 from '../assets/images/IMG-20260927-WA001.jpg'
import photo2 from '../assets/images/IMG-20260927-WA002.jpg'
import photo3 from '../assets/images/IMG-20260927-WA003.jpg'
import photo4 from '../assets/images/IMG-20260927-WA004.jpg'
import photo5 from '../assets/images/IMG-20260927-WA005.jpg'
import photo6 from '../assets/images/IMG-20260927-WA006.jpg'
import photo7 from '../assets/images/IMG-20260927-WA007.jpg'
import photo8 from '../assets/images/IMG-20260927-WA008.jpg'
import photo9 from '../assets/images/IMG-20260927-WA009.jpg'
import photo10 from '../assets/images/IMG-20260927-WA010.jpg'
import photo11 from '../assets/images/IMG-20260927-WA0045.jpg'
import photo12 from '../assets/images/IMG-20260927-WA0046.jpg'
import photo13 from '../assets/images/IMG-20260927-WA0047.jpg'
import photo14 from '../assets/images/IMG-20260927-WA0048.jpg'
import photo15 from '../assets/images/IMG-20260927-WA0049.jpg'
import photo16 from '../assets/images/IMG-20260927-WA0050.jpg'
import photo17 from '../assets/images/IMG-20260927-WA0051.jpg'
import photo18 from '../assets/images/IMG-20260927-WA0052.jpg'
import photo19 from '../assets/images/IMG-20260927-WA0053.jpg'
import photo20 from '../assets/images/IMG-20260927-WA0054.jpg'
import photo21 from '../assets/images/IMG-20260927-WA0056.jpg'
import photo22 from '../assets/images/IMG-20260927-WA0057.jpg'

const emit = defineEmits(['next'])

const photos = [
    { src: photo1, caption: 'pretty girl ♡' },
    { src: photo2, caption: 'look at you!' },
    { src: photo3, caption: 'cutieee' },
    { src: photo4, caption: 'my favorite smile' },
    { src: photo5, caption: 'so pretty...' },
    { src: photo6, caption: 'my girl ♡' },

    { src: photo7, caption: 'adorable.' },
    { src: photo8, caption: 'how are you this pretty?' },
    { src: photo9, caption: 'another favorite ♡' },
    { src: photo10, caption: 'beautiful as always' },
    { src: photo11, caption: 'that smile >>>' },
    { src: photo12, caption: 'pretty pretty pretty' },

    { src: photo13, caption: 'my favorite human' },
    { src: photo14, caption: 'cute.' },
    { src: photo15, caption: 'love this one ♡' },
    { src: photo16, caption: 'look at herrr' },
    { src: photo17, caption: 'gorgeous.' },
    { src: photo18, caption: 'still my favorite' },

    { src: photo19, caption: 'birthday girl ♡' },
    { src: photo20, caption: 'you.' },
    { src: photo21, caption: 'always pretty.' },
    { src: photo22, caption: 'and my favorite one ♡' },
]

const currentSlide = ref(0)
const selectedPhoto = ref(null)

const photosPerSlide = 6

const totalSlides = computed(() => {
    return Math.ceil(photos.length / photosPerSlide)
})

const visiblePhotos = computed(() => {
    const start = currentSlide.value * photosPerSlide
    const end = start + photosPerSlide

    return photos.slice(start, end)
})

const isLastSlide = computed(() => {
    return currentSlide.value === totalSlides.value - 1
})

const nextSlide = () => {
    if (!isLastSlide.value) {
        currentSlide.value++
    } else {
        emit('next')
    }
}

const previousSlide = () => {
    if (currentSlide.value > 0) {
        currentSlide.value--
    }
}

const openPhoto = (photo) => {
    selectedPhoto.value = photo
}

const closePhoto = () => {
    selectedPhoto.value = null
}
</script>

<template>

    <section class="recap-page">

        <div class="scrapbook">

            <!-- TITLE -->

            <div class="title-area">

                <span class="star">✦</span>

                <h1>RECAP</h1>

                <p>
                    some pictures of my favorite girl.
                </p>

            </div>


            <!-- DECORATION -->

            <div class="doodle doodle-one">
                ♡
            </div>

            <div class="doodle doodle-two">
                ★
            </div>

            <div class="doodle doodle-three">
                ✦
            </div>


            <!-- PHOTO GRID -->

            <Transition name="slide" mode="out-in">

                <div :key="currentSlide" class="photo-grid">

                    <div v-for="(photo, index) in visiblePhotos" :key="photo.src" class="polaroid"
                        :class="`photo-${index + 1}`" @click="openPhoto(photo)">

                        <div class="tape"></div>

                        <img :src="photo.src" :alt="photo.caption" />

                        <p>
                            {{ photo.caption }}
                        </p>

                    </div>

                </div>

            </Transition>

            <div class="page-indicator">

                <span v-for="page in totalSlides" :key="page" :class="{ active: page - 1 === currentSlide }">
                    ●
                </span>

            </div>


            <!-- BOTTOM TEXT -->

            <div class="bottom-message">

                <span>
                    01
                </span>

                <p>
                    a small collection of
                    <br>
                    a very pretty human ♡
                </p>

            </div>


            <div class="navigation">

                <button v-if="currentSlide > 0" class="nav-button" @click="previousSlide">
                    ← BACK
                </button>

                <button class="nav-button" @click="nextSlide">
                    {{ isLastSlide ? 'CONTINUE →' : 'NEXT →' }}
                </button>

            </div>

        </div>


        <!-- PHOTO MODAL -->

        <Transition name="modal">

            <div v-if="selectedPhoto" class="photo-modal" @click="closePhoto">

                <div class="modal-polaroid" @click.stop>

                    <button class="close-button" @click="closePhoto">
                        ×
                    </button>

                    <img :src="selectedPhoto.src" :alt="selectedPhoto.caption" />

                    <p>
                        {{ selectedPhoto.caption }}
                    </p>

                </div>

            </div>

        </Transition>

    </section>

</template>


<style scoped>
/* ============================= */
/* BACKGROUND */
/* ============================= */

/* PAGE INDICATOR */

.page-indicator {
    display: flex;
    justify-content: center;
    gap: 10px;

    margin-top: 45px;
}

.page-indicator span {
    color: #666;

    font-size: 12px;

    transition: .3s;
}

.page-indicator span.active {
    color: white;

    transform: scale(1.5);
}


/* NAVIGATION */

.navigation {
    margin-top: 35px;

    display: flex;
    justify-content: center;

    gap: 25px;
}

.nav-button {
    background: white;

    color: black;

    border: 3px solid black;

    padding: 12px 25px;

    font-family:
        "Courier New",
        monospace;

    font-size: 14px;

    font-weight: bold;

    cursor: pointer;

    box-shadow:
        6px 6px 0 #777;

    transition: .2s;
}

.nav-button:hover {
    transform:
        translateY(-4px);

    box-shadow:
        6px 10px 0 #777;
}


/* SLIDE ANIMATION */

.slide-enter-active,
.slide-leave-active {
    transition: .35s ease;
}

.slide-enter-from {
    opacity: 0;

    transform:
        translateX(50px);
}

.slide-leave-to {
    opacity: 0;

    transform:
        translateX(-50px);
}

.recap-page {
    width: 100%;
    min-height: 100vh;

    display: flex;
    justify-content: center;
    align-items: center;

    padding: 35px;

    background-color: #dfcbbb;

    background-image:
        linear-gradient(rgba(120, 80, 60, .1) 1px,
            transparent 1px),
        linear-gradient(90deg,
            rgba(120, 80, 60, .1) 1px,
            transparent 1px);

    background-size: 35px 35px;
}


/* ============================= */
/* SCRAPBOOK */
/* ============================= */

.scrapbook {
    width: min(1000px, 95%);

    min-height: 700px;

    position: relative;

    padding:
        55px 65px 80px;

    overflow: hidden;

    background:
        #191919;

    border:
        9px solid white;

    box-shadow:
        13px 13px 0 rgba(0, 0, 0, .25);
}


/* ============================= */
/* TITLE */
/* ============================= */

.title-area {
    text-align: center;

    color: white;

    margin-bottom: 50px;

    position: relative;

    z-index: 3;
}


.title-area h1 {
    margin: 0;

    display: inline-block;

    background: white;

    color: #111;

    padding:
        5px 18px;

    font-family:
        Impact,
        sans-serif;

    font-size:
        clamp(45px, 7vw, 80px);

    letter-spacing:
        8px;

    transform:
        rotate(-2deg);

    box-shadow:
        7px 7px 0 #777;
}


.title-area p {
    margin-top:
        25px;

    font-family:
        "Courier New",
        monospace;

    font-size:
        16px;

    letter-spacing:
        2px;

    color:
        #ddd;
}


.star {
    position:
        absolute;

    margin-left:
        -50px;

    margin-top:
        -25px;

    font-size:
        45px;

    color:
        #eee;
}


/* ============================= */
/* PHOTO GRID */
/* ============================= */

.photo-grid {
    display: grid;

    grid-template-columns:
        repeat(3, 1fr);

    gap:
        45px 35px;

    max-width:
        800px;

    margin:
        auto;
}


/* ============================= */
/* POLAROID */
/* ============================= */

.polaroid {
    background:
        #f5f1e8;

    padding:
        12px 12px 20px;

    position:
        relative;

    cursor:
        pointer;

    box-shadow:
        8px 10px 0 rgba(0, 0, 0, .45);

    transition:
        transform .25s,
        box-shadow .25s;

    animation:
        photoAppear .7s ease both;
}


.polaroid img {
    display: block;

    width: 100%;
    height: 220px;

    object-fit:
        cover;

    filter:
        grayscale(15%) contrast(1.05);
}


.polaroid p {
    margin:
        15px 5px 0;

    text-align:
        center;

    color:
        #222;

    font-family:
        "Courier New",
        monospace;

    font-size:
        14px;

    font-weight:
        bold;
}


.polaroid:hover {
    z-index: 10;

    transform:
        rotate(0deg) scale(1.08);

    box-shadow:
        14px 16px 0 rgba(0, 0, 0, .4);
}


/* ============================= */
/* RANDOM ROTATION */
/* ============================= */

.photo-1 {
    transform:
        rotate(-5deg);

    animation-delay:
        .1s;
}


.photo-2 {
    transform:
        rotate(3deg) translateY(20px);

    animation-delay:
        .2s;
}


.photo-3 {
    transform:
        rotate(-2deg);

    animation-delay:
        .3s;
}


.photo-4 {
    transform:
        rotate(4deg);

    animation-delay:
        .4s;
}


.photo-5 {
    transform:
        rotate(-4deg) translateY(15px);

    animation-delay:
        .5s;
}


.photo-6 {
    transform:
        rotate(3deg);

    animation-delay:
        .6s;
}


/* ============================= */
/* TAPE */
/* ============================= */

.tape {
    width:
        80px;

    height:
        25px;

    position:
        absolute;

    top:
        -14px;

    left:
        50%;

    transform:
        translateX(-50%) rotate(-3deg);

    z-index:
        3;

    background:
        rgba(220,
            200,
            165,
            .75);
}


/* ============================= */
/* DECORATIONS */
/* ============================= */

.doodle {
    position:
        absolute;

    color:
        white;

    opacity:
        .75;

    font-family:
        Georgia,
        serif;
}


.doodle-one {
    left:
        30px;

    top:
        220px;

    font-size:
        65px;

    transform:
        rotate(-20deg);
}


.doodle-two {
    right:
        30px;

    top:
        300px;

    font-size:
        40px;

    transform:
        rotate(15deg);
}


.doodle-three {
    right:
        80px;

    bottom:
        60px;

    font-size:
        55px;
}


/* ============================= */
/* BOTTOM MESSAGE */
/* ============================= */

.bottom-message {
    margin-top:
        60px;

    color:
        white;

    display:
        flex;

    align-items:
        center;

    gap:
        25px;

    font-family:
        "Courier New",
        monospace;
}


.bottom-message span {
    font-family:
        Impact,
        sans-serif;

    font-size:
        60px;

    opacity:
        .25;
}


.bottom-message p {
    font-size:
        13px;

    line-height:
        1.6;

    letter-spacing:
        1px;
}


/* ============================= */
/* NEXT BUTTON */
/* ============================= */

.next-button {
    position:
        absolute;

    right:
        40px;

    bottom:
        40px;

    padding:
        13px 28px;

    background:
        white;

    color:
        black;

    border:
        3px solid black;

    font-family:
        "Courier New",
        monospace;

    font-weight:
        bold;

    font-size:
        16px;

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


/* ============================= */
/* MODAL */
/* ============================= */

.photo-modal {
    position:
        fixed;

    inset:
        0;

    z-index:
        100;

    display:
        flex;

    justify-content:
        center;

    align-items:
        center;

    padding:
        25px;

    background:
        rgba(0, 0, 0, .88);

    backdrop-filter:
        blur(6px);
}


.modal-polaroid {
    width:
        min(430px, 90%);

    padding:
        15px 15px 30px;

    background:
        #f5f1e8;

    position:
        relative;

    transform:
        rotate(-2deg);

    box-shadow:
        15px 15px 0 rgba(255, 255, 255, .15);
}


.modal-polaroid img {
    width:
        100%;

    max-height:
        65vh;

    display:
        block;

    object-fit:
        cover;
}


.modal-polaroid p {
    color:
        #222;

    text-align:
        center;

    font-family:
        "Courier New",
        monospace;

    font-size:
        17px;

    font-weight:
        bold;

    margin:
        20px 0 0;
}


.close-button {
    width:
        38px;

    height:
        38px;

    position:
        absolute;

    right:
        -18px;

    top:
        -18px;

    z-index:
        5;

    border:
        3px solid black;

    border-radius:
        50%;

    background:
        white;

    color:
        black;

    font-size:
        25px;

    font-weight:
        bold;

    cursor:
        pointer;
}


/* ============================= */
/* TRANSITION */
/* ============================= */

.modal-enter-active,
.modal-leave-active {
    transition:
        .3s ease;
}


.modal-enter-from,
.modal-leave-to {
    opacity:
        0;
}


.modal-enter-from .modal-polaroid {
    transform:
        scale(.7) rotate(-10deg);
}


/* ============================= */
/* ANIMATION */
/* ============================= */

@keyframes photoAppear {

    from {
        opacity:
            0;

        transform:
            translateY(50px) rotate(0deg) scale(.8);
    }

}


/* ============================= */
/* TABLET */
/* ============================= */

@media (max-width: 850px) {

    .photo-grid {
        grid-template-columns:
            repeat(2, 1fr);
    }

}


/* ============================= */
/* MOBILE */
/* ============================= */

@media (max-width: 550px) {

    .recap-page {
        padding:
            15px;
    }


    .scrapbook {
        width:
            100%;

        padding:
            50px 25px 120px;
    }


    .title-area {
        margin-bottom:
            40px;
    }


    .title-area h1 {
        font-size:
            45px;

        letter-spacing:
            5px;
    }


    .title-area p {
        font-size:
            12px;
    }


    .photo-grid {
        grid-template-columns:
            repeat(2, 1fr);

        gap:
            35px 15px;
    }


    .polaroid {
        padding:
            8px 8px 15px;
    }


    .polaroid img {
        height:
            180px;
    }


    .polaroid p {
        font-size:
            11px;
    }


    .doodle {
        display:
            none;
    }


    .bottom-message {
        margin-top:
            50px;
    }


    .bottom-message span {
        font-size:
            45px;
    }


    .bottom-message p {
        font-size:
            10px;
    }


    .next-button {
        right:
            25px;

        bottom:
            30px;
    }

}
</style>