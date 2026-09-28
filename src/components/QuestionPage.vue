<script setup>
import { ref } from 'vue'

const emit = defineEmits(['next'])

const questionStep = ref(1)

const chooseLove = () => {
    questionStep.value = 2
}

const chooseOption = () => {
    questionStep.value = 3
}

const continueStory = () => {
    emit('next')
}
</script>

<template>
    <section class="question-page">

        <div class="question-card">

            <!-- ==================== -->
            <!-- QUESTION 1 -->
            <!-- ==================== -->

            <div v-if="questionStep === 1" class="question-content">
                <div class="character character-left">
                    <div class="character-placeholder">
                        Farhan
                    </div>
                </div>

                <div class="dialog-area">

                    <div class="speech-box">
                        Do you want to know how much
                        <br />
                        I love you babe?
                    </div>

                    <div class="answer-container">

                        <button class="pixel-button" @click="chooseLove">
                            YES
                        </button>

                        <button class="pixel-button tilted" @click="chooseLove">
                            DEFINITELY
                        </button>

                    </div>

                </div>

                <div class="character character-right">
                    <div class="character-placeholder">
                        Indi
                    </div>
                </div>

            </div>


            <!-- ==================== -->
            <!-- QUESTION 2 -->
            <!-- ==================== -->

            <div v-if="questionStep === 2" class="question-content second-question">

                <div class="character character-left">
                    <div class="character-placeholder">
                        Farhan
                    </div>
                </div>

                <div class="dialog-area">

                    <div class="speech-box">
                        But first...
                        <br />
                        you have to choose one
                        <br />
                        from these two options.
                    </div>

                    <div class="answer-container">

                        <button class="pixel-button" @click="chooseOption">
                            Are you
                            <br />
                            crazy?
                        </button>
                        <button class="pixel-button" @click="chooseOption">
                            Support
                            <br />
                            LGBT?
                        </button>

                    </div>

                </div>

                <div class="character character-right">
                    <div class="character-placeholder">
                        Indi
                    </div>
                </div>

            </div>


            <!-- ==================== -->
            <!-- JOKE / RESULT -->
            <!-- ==================== -->

            <div v-if="questionStep === 3" class="result-content">

                <div class="cat">
                    ฅ^•ﻌ•^ฅ
                </div>

                <div class="small-speech">
                    Ok sorry babe...
                    <br />
                    no more jokes 😭
                </div>

                <div class="main-speech">
                    Let's start kiddo.
                </div>

                <button class="open-button" @click="continueStory">
                    OPEN
                </button>

            </div>

        </div>

    </section>
</template>


<style scoped>
/* ========================= */
/* BACKGROUND */
/* ========================= */

.question-page {
    min-height: 100vh;

    display: flex;
    justify-content: center;
    align-items: center;

    padding: 30px;

    background-color: #e4d1c0;

    background-image:
        linear-gradient(90deg,
            rgba(120, 80, 60, 0.12) 50%,
            transparent 50%),
        linear-gradient(rgba(120, 80, 60, 0.12) 50%,
            transparent 50%);

    background-size: 80px 80px;
}


/* ========================= */
/* CARD */
/* ========================= */

.question-card {

    width: min(900px, 95%);
    min-height: 520px;

    background:

        radial-gradient(circle at 30% 20%,
            #242424,
            transparent 40%),

        #0c0c0c;

    border: 8px solid white;

    box-shadow:
        12px 12px 0 rgba(0, 0, 0, .25);

    position: relative;

    overflow: hidden;
}


/* ========================= */
/* QUESTION */
/* ========================= */

.question-content {

    min-height: 520px;

    display: flex;

    align-items: center;
    justify-content: space-between;

    padding: 40px;
}


/* ========================= */
/* CHARACTER */
/* ========================= */

.character {

    width: 170px;

    display: flex;
    align-items: flex-end;

    height: 350px;
}


.character-placeholder {

    width: 150px;
    height: 280px;

    background:
        linear-gradient(145deg,
            #333,
            #111);

    border: 3px solid white;

    display: flex;
    justify-content: center;
    align-items: center;

    color: white;

    font-family:
        "Courier New",
        monospace;

    font-weight: bold;

    box-shadow:
        8px 8px 0 #555;
}


.character-left {

    transform: rotate(-3deg);

}


.character-right {

    transform: rotate(3deg);

}


/* ========================= */
/* DIALOG */
/* ========================= */

.dialog-area {

    flex: 1;

    display: flex;
    flex-direction: column;

    align-items: center;

    gap: 40px;

    z-index: 2;
}


.speech-box {

    background: white;

    color: #111;

    padding: 22px 35px;

    text-align: center;

    font-family:
        Georgia,
        serif;

    font-size: 21px;

    line-height: 1.5;

    box-shadow:

        7px 7px 0 #aaa,

        14px 14px 0 #555;

    position: relative;
}


.speech-box::after {

    content: "";

    position: absolute;

    bottom: -20px;
    left: 50%;

    transform: translateX(-50%);

    border-left: 18px solid transparent;
    border-right: 18px solid transparent;

    border-top: 22px solid white;
}


/* ========================= */
/* ANSWER */
/* ========================= */

.answer-container {

    display: flex;

    gap: 30px;

    flex-wrap: wrap;

    justify-content: center;
}


.pixel-button {

    min-width: 140px;

    background: white;

    color: #111;

    border: 4px solid #111;

    padding: 13px 20px;

    font-family:
        "Courier New",
        monospace;

    font-size: 18px;

    font-weight: bold;

    cursor: pointer;

    box-shadow:

        5px 5px 0 white,

        9px 9px 0 #555;

    transition: .15s;
}


.pixel-button:hover {

    transform:
        translate(-3px, -3px);

    box-shadow:

        8px 8px 0 white,

        12px 12px 0 #555;
}


.pixel-button:active {

    transform:
        translate(5px, 5px);

    box-shadow: none;

}


.tilted {

    transform: rotate(3deg);

}


.tilted:hover {

    transform:
        rotate(3deg) translate(-3px, -3px);
}


/* ========================= */
/* RESULT */
/* ========================= */

.result-content {

    min-height: 520px;

    display: flex;

    flex-direction: column;

    justify-content: center;
    align-items: center;

    gap: 30px;

    position: relative;

    background:

        radial-gradient(circle,
            #222 1px,
            transparent 1px);

    background-size:
        25px 25px;
}


.cat {

    font-size: 70px;

    color: white;

    animation:
        catBounce 1.5s infinite;
}


.small-speech {

    position: absolute;

    top: 70px;
    left: 70px;

    background: white;

    padding:
        12px 22px;

    font-family:
        "Courier New",
        monospace;

    font-weight: bold;

    transform:
        rotate(-2deg);
}


.main-speech {

    background: white;

    padding:
        15px 35px;

    color: black;

    font-family:
        "Courier New",
        monospace;

    font-size: 20px;

    font-weight: bold;

    box-shadow:
        7px 7px 0 #777;
}


.open-button {

    background: white;

    color: black;

    border:
        4px solid black;

    padding:
        15px 45px;

    font-family:
        "Courier New",
        monospace;

    font-size: 25px;

    font-weight: bold;

    text-decoration:
        underline;

    cursor: pointer;

    box-shadow:
        8px 8px 0 #777;

    transition: .2s;
}


.open-button:hover {

    transform:
        scale(1.08) rotate(-2deg);

}


/* ========================= */
/* ANIMATION */
/* ========================= */

.question-content,
.result-content {

    animation:
        pageAppear .5s ease;
}


@keyframes pageAppear {

    from {

        opacity: 0;

        transform:
            translateY(20px);

    }

    to {

        opacity: 1;

        transform:
            translateY(0);

    }

}


@keyframes catBounce {

    0%,
    100% {

        transform:
            translateY(0);

    }

    50% {

        transform:
            translateY(-10px);

    }

}


/* ========================= */
/* MOBILE */
/* ========================= */

@media (max-width: 700px) {

    .question-page {

        padding: 15px;

    }


    .question-card {

        min-height: 650px;

    }


    .question-content {

        min-height: 650px;

        padding:
            30px 15px;

    }


    .character {

        width: 75px;

        height: 300px;

    }


    .character-placeholder {

        width: 70px;
        height: 230px;

        font-size: 11px;

    }


    .speech-box {

        padding:
            18px 15px;

        font-size: 16px;

    }


    .answer-container {

        gap: 20px;

    }


    .pixel-button {

        min-width: 120px;

        font-size: 14px;

    }


    .small-speech {

        left: 20px;
        top: 40px;

        font-size: 12px;

    }


    .main-speech {

        font-size: 16px;

    }

}
</style>