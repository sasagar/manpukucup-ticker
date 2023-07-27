<template>
    <div class="ticker-container">
        <img src="/images/rogo_inc_color.png" alt="まんぷく杯ロゴ" id="logo">
        <div class="ticker-right">
            <TeamContainer v-bind:team="now" :show="isShow"/>
            <CharactorContainer :show="isShow" />
        </div>
    </div>
</template>

<script setup>
import {
    ref,
    onMounted,
    computed
} from "vue";

import TeamContainer from "./TeamContainer.vue";
import CharactorContainer from "./CharactorContainer.vue";
import solo from "../../assets/json/12th/solo.json";
import pair from "../../assets/json/12th/pair.json";
import team from "../../assets/json/12th/team.json";
import extra from "../../assets/json/12th/extra.json";

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
    background-image: url(/images/12th/ticker-bg.png);
    background-position: center;
    position: absolute;
    bottom: 0;
    left: 0;
    overflow: hidden;
    flex: 1;
}

#logo {
    position: absolute;
    left: 50px;
    top: 50px;
    width: 200px;
    z-index: 5;
}

.ticker-right {
    width: 100%;
    display: flex;
    justify-content: space-between;
}
</style>