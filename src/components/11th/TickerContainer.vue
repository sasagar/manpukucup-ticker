<template>
    <div class="ticker-container">
        <img src="@/assets/images/rogo_inc_color.png" alt="まんぷく杯ロゴ" id="logo">
        <img src="@/assets/images/11th/sakura-front.png" alt="桜" id="sakura1">
        <img src="@/assets/images/11th/sakura-front-front.png" alt="桜" id="sakura2">
        <transition name="team-container" class="team-container" appear>
            <TeamContainer v-bind:team="now" v-if="isShow" />
        </transition>
    </div>
</template>

<script setup>
import {
    ref,
    onMounted,
    computed
} from "vue";

import TeamContainer from "./TeamContainer";
import solo from "../../assets/json/solo.json";
import pair from "../../assets/json/pair.json";
import team from "../../assets/json/team.json";
import extra from "../../assets/json/extra.json";

const isShow = ref(true);
const solos = solo.solos;
const pairs = pair.pairs;
const teams = team.teams;
const extras = extra.extras;

const counter = ref(0);
const series = ref("solo");

const now = computed(() => {
    let data;
    switch (series.value) {
        case "solo":
            data = solos[counter.value];
            break;
        case "pair":
            data = pairs[counter.value];
            break;
        case "team":
            data = teams[counter.value];
            break;
        case "extra":
            data = extras[counter.value];
            break;
    }
    return data;
});

const length = computed(() => {
    let data;
    switch (series.value) {
        case "solo":
            data = solos.length;
            break;
        case "pair":
            data = pairs.length;
            break;
        case "team":
            data = teams.length;
            break;
        case "extra":
            data = extras.length;
            break;
    }
    return data;
})

const changer = function() {
    window.setInterval(async () => {
        isShow.value = false // 1回画面から消す
        counter.value++
        if (length.value <= counter.value) {
            switch (series.value) {
                case "solo":
                    series.value = "pair";
                    break;
                case "pair":
                    series.value = "team";
                    break;
                case "team":
                    series.value = "extra";
                    break;
                case "extra":
                    series.value = "solo";
                    break;
            }
            counter.value = 0
        }
        // console.log(counter.value);
        setTimeout(() => {
            isShow.value = true;
        }, 500);
    }, 10000)
}

onMounted(() => {
    changer();
})

</script>

<style scoped>
.ticker-container {
    width: 1920px;
    height: 200px;
    background-image: url(~@/assets/images/11th/bg.jpg);
    background-position: center;
    position: absolute;
    bottom: 0;
    left: 0;
    overflow: hidden;
}

#logo {
    position: absolute;
    left: 50px;
    top: 50px;
    width: 200px;
    z-index: 5;
}

#sakura1 {
    position: absolute;
    left: -5px;
    top: -50px;
    width: 350px;
    z-index: 1;
    transform-origin: left top;
    animation: infinite sakura1 10s ease-in-out;
}

#sakura2 {
    position: absolute;
    left: -50px;
    top: 50px;
    width: 300px;
    z-index: 2;
    transform-origin: left top;
    animation: infinite sakura2 15s ease-in-out;
}

.team-container {
    transition: all .5s ease;
    opacity: 1;
    width: calc(100% - 300px);
    margin-left: 300px;
    /* position: absolute; */
    z-index: 10;
    display: flex;
    justify-content: center;
}

.team-container-enter-from {
    transform: translateX(100px);
    opacity: 0;
}
.team-container-leave-to {
    transform: translateX(-100px);
    opacity: 0;
}

@keyframes sakura1 {
    0% {
        transform: rotate(4deg);
    }
    28% {
        transform: rotate(-2deg);
    }
    48% {
        transform: rotate(1deg);
    }
    77% {
        transform: rotate(-3deg);
    }
    100% {
        transform: rotate(4deg);
    }
}

@keyframes sakura2 {
    0% {
        transform: rotate(-20deg);
    }
    28% {
        transform: rotate(-16deg);
    }
    48% {
        transform: rotate(-23deg);
    }
    77% {
        transform: rotate(-18deg);
    }
    100% {
        transform: rotate(-20deg);
    }
}

</style>