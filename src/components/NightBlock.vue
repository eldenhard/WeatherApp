<template>
    <div>
        <Clock />
        <div style="z-index: 0.5">
        <div class="shootingStarContainer">
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
        </div>
        <div class="shootingStarContainer">
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
        </div>
        <div class="shootingStarContainer">
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
            <div class="shootingStar"></div>
        </div>


        <div class="stars"></div>
        <div class="twinkleMask"></div>
        <div class="twinkleMask2"></div>
        <div class="clouds"></div>

        <div class="fogContainer">
            <div class="fog"></div>
        </div>
    </div>
    </div>
</template>
<script>
import Clock from '@/components/Clock.vue'
export default {
    name: 'Night',
    components: { Clock }
}
</script>
<style scoped>
* {
    margin: 0;
    padding: 0;
}

body {
    background: #000;
    height: 100vh;
    overflow: hidden;
}

.shootingStarContainer:nth-child(1) {
    position: absolute;
    width: 100%;
    height: 50%;
    transform: rotate(16deg);
    z-index: 10;
}

.shootingStarContainer:nth-child(2) {
    position: absolute;
    width: 100%;
    height: 50%;
    transform: rotate(29deg);
    z-index: 10;
}

.shootingStarContainer:nth-child(3) {
    position: absolute;
    width: 100%;
    height: 50%;
    transform: rotate(16deg);
    z-index: 10;
}

.shootingStar {
    position: absolute;
    height: 1px;
    background: linear-gradient(-70deg, #ffebeb, black);
}

.shootingStarContainer:nth-child(1) .shootingStar:nth-child(1) {
    left: calc(19%);
    top: calc(4%);
    -webkit-animation: shootingFrames 2294ms ease-in-out 23860ms;
    animation: shootingFrames 2294ms ease-in-out 23860ms;
    opacity: 0.41;
}

.shootingStarContainer:nth-child(1) .shootingStar:nth-child(2) {
    left: calc(36%);
    top: calc(38%);
    -webkit-animation: shootingFrames 1413ms ease-in-out 11638ms;
    animation: shootingFrames 1413ms ease-in-out 11638ms;
    opacity: 0.67;
}

.shootingStarContainer:nth-child(1) .shootingStar:nth-child(3) {
    left: calc(38%);
    top: calc(27%);
    -webkit-animation: shootingFrames 2010ms ease-in-out 21490ms;
    animation: shootingFrames 2010ms ease-in-out 21490ms;
    opacity: 0.86;
}

.shootingStarContainer:nth-child(1) .shootingStar:nth-child(4) {
    left: calc(3%);
    top: calc(74%);
    -webkit-animation: shootingFrames 1601ms ease-in-out 1291ms;
    animation: shootingFrames 1601ms ease-in-out 1291ms;
    opacity: 0.33;
}

.shootingStarContainer:nth-child(1) .shootingStar:nth-child(5) {
    left: calc(6%);
    top: calc(35%);
    -webkit-animation: shootingFrames 1648ms ease-in-out 6396ms;
    animation: shootingFrames 1648ms ease-in-out 6396ms;
    opacity: 0.34;
}

.shootingStarContainer:nth-child(1) .shootingStar:nth-child(6) {
    left: calc(43%);
    top: calc(36%);
    -webkit-animation: shootingFrames 1679ms ease-in-out 10755ms;
    animation: shootingFrames 1679ms ease-in-out 10755ms;
    opacity: 0.83;
}

.shootingStarContainer:nth-child(1) .shootingStar:nth-child(7) {
    left: calc(33%);
    top: calc(76%);
    -webkit-animation: shootingFrames 1366ms ease-in-out 43917ms;
    animation: shootingFrames 1366ms ease-in-out 43917ms;
    opacity: 0.64;
}

.shootingStarContainer:nth-child(1) .shootingStar:nth-child(8) {
    left: calc(19%);
    top: calc(16%);
    -webkit-animation: shootingFrames 1410ms ease-in-out 43169ms;
    animation: shootingFrames 1410ms ease-in-out 43169ms;
    opacity: 0.17;
}

.shootingStarContainer:nth-child(1) .shootingStar:nth-child(9) {
    left: calc(34%);
    top: calc(93%);
    -webkit-animation: shootingFrames 1465ms ease-in-out 9061ms;
    animation: shootingFrames 1465ms ease-in-out 9061ms;
    opacity: 0.8;
}

.shootingStarContainer:nth-child(1) .shootingStar:nth-child(10) {
    left: calc(39%);
    top: calc(7%);
    -webkit-animation: shootingFrames 851ms ease-in-out 20915ms;
    animation: shootingFrames 851ms ease-in-out 20915ms;
    opacity: 0.24;
}

.shootingStarContainer:nth-child(2) .shootingStar:nth-child(1) {
    left: calc(24%);
    top: calc(14%);
    -webkit-animation: shootingFrames 1069ms ease-in-out 25308ms;
    animation: shootingFrames 1069ms ease-in-out 25308ms;
    opacity: 0.31;
}

.shootingStarContainer:nth-child(2) .shootingStar:nth-child(2) {
    left: calc(16%);
    top: calc(88%);
    -webkit-animation: shootingFrames 939ms ease-in-out 48047ms;
    animation: shootingFrames 939ms ease-in-out 48047ms;
    opacity: 0.85;
}

.shootingStarContainer:nth-child(2) .shootingStar:nth-child(3) {
    left: calc(30%);
    top: calc(13%);
    -webkit-animation: shootingFrames 2537ms ease-in-out 47297ms;
    animation: shootingFrames 2537ms ease-in-out 47297ms;
    opacity: 0.46;
}

.shootingStarContainer:nth-child(2) .shootingStar:nth-child(4) {
    left: calc(44%);
    top: calc(84%);
    -webkit-animation: shootingFrames 1036ms ease-in-out 26438ms;
    animation: shootingFrames 1036ms ease-in-out 26438ms;
    opacity: 0.52;
}

.shootingStarContainer:nth-child(2) .shootingStar:nth-child(5) {
    left: calc(6%);
    top: calc(54%);
    -webkit-animation: shootingFrames 1427ms ease-in-out 49081ms;
    animation: shootingFrames 1427ms ease-in-out 49081ms;
    opacity: 0.58;
}

.shootingStarContainer:nth-child(2) .shootingStar:nth-child(6) {
    left: calc(28%);
    top: calc(17%);
    -webkit-animation: shootingFrames 2363ms ease-in-out 1703ms;
    animation: shootingFrames 2363ms ease-in-out 1703ms;
    opacity: 0.58;
}

.shootingStarContainer:nth-child(2) .shootingStar:nth-child(7) {
    left: calc(41%);
    top: calc(6%);
    -webkit-animation: shootingFrames 1655ms ease-in-out 41218ms;
    animation: shootingFrames 1655ms ease-in-out 41218ms;
    opacity: 0.51;
}

.shootingStarContainer:nth-child(2) .shootingStar:nth-child(8) {
    left: calc(10%);
    top: calc(30%);
    -webkit-animation: shootingFrames 1386ms ease-in-out 58787ms;
    animation: shootingFrames 1386ms ease-in-out 58787ms;
    opacity: 0.79;
}

.shootingStarContainer:nth-child(2) .shootingStar:nth-child(9) {
    left: calc(38%);
    top: calc(90%);
    -webkit-animation: shootingFrames 1651ms ease-in-out 55675ms;
    animation: shootingFrames 1651ms ease-in-out 55675ms;
    opacity: 0.31;
}

.shootingStarContainer:nth-child(2) .shootingStar:nth-child(10) {
    left: calc(41%);
    top: calc(85%);
    -webkit-animation: shootingFrames 2467ms ease-in-out 49622ms;
    animation: shootingFrames 2467ms ease-in-out 49622ms;
    opacity: 0.8;
}

.shootingStarContainer:nth-child(3) .shootingStar:nth-child(1) {
    left: calc(40%);
    top: calc(97%);
    -webkit-animation: shootingFrames 1962ms ease-in-out 38828ms;
    animation: shootingFrames 1962ms ease-in-out 38828ms;
    opacity: 0.5;
}

.shootingStarContainer:nth-child(3) .shootingStar:nth-child(2) {
    left: calc(22%);
    top: calc(47%);
    -webkit-animation: shootingFrames 900ms ease-in-out 24957ms;
    animation: shootingFrames 900ms ease-in-out 24957ms;
    opacity: 0.73;
}

.shootingStarContainer:nth-child(3) .shootingStar:nth-child(3) {
    left: calc(48%);
    top: calc(45%);
    -webkit-animation: shootingFrames 2240ms ease-in-out 20778ms;
    animation: shootingFrames 2240ms ease-in-out 20778ms;
    opacity: 0.19;
}

.shootingStarContainer:nth-child(3) .shootingStar:nth-child(4) {
    left: calc(25%);
    top: calc(73%);
    -webkit-animation: shootingFrames 1009ms ease-in-out 58746ms;
    animation: shootingFrames 1009ms ease-in-out 58746ms;
    opacity: 0.8;
}

.shootingStarContainer:nth-child(3) .shootingStar:nth-child(5) {
    left: calc(30%);
    top: calc(35%);
    -webkit-animation: shootingFrames 2228ms ease-in-out 4060ms;
    animation: shootingFrames 2228ms ease-in-out 4060ms;
    opacity: 0.79;
}

.shootingStarContainer:nth-child(3) .shootingStar:nth-child(6) {
    left: calc(30%);
    top: calc(69%);
    -webkit-animation: shootingFrames 1177ms ease-in-out 55352ms;
    animation: shootingFrames 1177ms ease-in-out 55352ms;
    opacity: 0.61;
}

.shootingStarContainer:nth-child(3) .shootingStar:nth-child(7) {
    left: calc(39%);
    top: calc(98%);
    -webkit-animation: shootingFrames 1117ms ease-in-out 49566ms;
    animation: shootingFrames 1117ms ease-in-out 49566ms;
    opacity: 0.21;
}

.shootingStarContainer:nth-child(3) .shootingStar:nth-child(8) {
    left: calc(50%);
    top: calc(71%);
    -webkit-animation: shootingFrames 1320ms ease-in-out 16507ms;
    animation: shootingFrames 1320ms ease-in-out 16507ms;
    opacity: 0.21;
}

.shootingStarContainer:nth-child(3) .shootingStar:nth-child(9) {
    left: calc(23%);
    top: calc(95%);
    -webkit-animation: shootingFrames 2713ms ease-in-out 40914ms;
    animation: shootingFrames 2713ms ease-in-out 40914ms;
    opacity: 0.49;
}

.shootingStarContainer:nth-child(3) .shootingStar:nth-child(10) {
    left: calc(38%);
    top: calc(43%);
    -webkit-animation: shootingFrames 1641ms ease-in-out 21112ms;
    animation: shootingFrames 1641ms ease-in-out 21112ms;
    opacity: 0.33;
}

@-webkit-keyframes shootingFrames {
    0% {
        transform: translateX(0);
        width: 0;
    }

    30% {
        width: 200px;
    }

    100% {
        width: 0;
        transform: translateX(801px);
    }
}

@keyframes shootingFrames {
    0% {
        transform: translateX(0);
        width: 0;
    }

    30% {
        width: 200px;
    }

    100% {
        width: 0;
        transform: translateX(801px);
    }
}

.stars,
.twinkleMask,
.twinkleMask2,
.clouds {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    width: 100%;
    height: 100%;
    display: block;
}

.stars {
    background: #000 url('@/assets/stars.jpg') repeat top center;
    z-index: 0;
}

.twinkleMask {
    background: transparent url("https://wolf.drjm.co.uk/nightsky/twinklemask.png") repeat top center;
    z-index: 1;
    -webkit-animation: twinkleFrames 700s linear infinite;
    animation: twinkleFrames 700s linear infinite;
}

.twinkleMask2 {
    background: transparent url("https://wolf.drjm.co.uk/nightsky/twinkleMask2.png") repeat top center;
    z-index: 2;
    height: 100%;
    -webkit-animation: twinkleFrames2 300s linear infinite;
    animation: twinkleFrames2 300s linear infinite;
}

.clouds {
    background: transparent url("https://wolf.drjm.co.uk/nightsky/clouds.png") repeat top center;
    z-index: 3;
    height: 100%;
    -webkit-animation: cloudsFrames 300s linear infinite;
    animation: cloudsFrames 300s linear infinite;
}

.fogContainer {
    width: 100vw;
    height: 100vh;
    overflow: hidden;
    position: relative;
    z-index: 7;
}

.fog {
    position: absolute;
    left: -50%;
    top: -30%;
    width: 200%;
    height: 200%;
    -webkit-animation-name: fogFrames;
    animation-name: fogFrames;
    -webkit-animation-duration: 60s;
    animation-duration: 60s;
    -webkit-animation-timing-function: linear;
    animation-timing-function: linear;
    -webkit-animation-iteration-count: infinite;
    animation-iteration-count: infinite;
    -webkit-animation-direction: alternate;
    animation-direction: alternate;
    background: linear-gradient(-5deg, #00000000 0%, #ffffff15 40%, #74590121 45%, #8b845b21 55%, #00000000 70%);
}

@-webkit-keyframes fogFrames {
    0% {
        transform: none;
    }

    10% {
        transform: scaleY(0.75) translate(5%, -2%) rotate(15deg);
    }

    25% {
        transform: scaleY(1) translate(10%, 7%);
    }

    50% {
        transform: scaleY(0.5) rotate(-15deg);
    }

    75% {
        transform: scaleY(0.2) translate(7%, -2%);
    }

    100% {
        transform: none;
    }
}

@keyframes fogFrames {
    0% {
        transform: none;
    }

    10% {
        transform: scaleY(0.75) translate(5%, -2%) rotate(15deg);
    }

    25% {
        transform: scaleY(1) translate(10%, 7%);
    }

    50% {
        transform: scaleY(0.5) rotate(-15deg);
    }

    75% {
        transform: scaleY(0.2) translate(7%, -2%);
    }

    100% {
        transform: none;
    }
}

@-webkit-keyframes twinkleFrames {
    from {
        background-position: 0 0;
    }

    to {
        background-position: -10000px 5000px;
    }
}

@keyframes twinkleFrames {
    from {
        background-position: 0 0;
    }

    to {
        background-position: -10000px 5000px;
    }
}

@-webkit-keyframes twinkleFrames2 {
    from {
        background-position: 0 0;
    }

    to {
        background-position: 10000px 5000px;
    }
}

@keyframes twinkleFrames2 {
    from {
        background-position: 0 0;
    }

    to {
        background-position: 10000px 5000px;
    }
}

@-webkit-keyframes cloudsFrames {
    from {
        background-position: 0 0;
    }

    to {
        background-position: 10000px 0;
    }
}

@keyframes cloudsFrames {
    from {
        background-position: 0 0;
    }

    to {
        background-position: 10000px 0;
    }
}
</style>
