<template>
    <transition name="charactor" appear>
        <img :src="charactor()" alt="キャラクター" class="charactor" v-if="props.show" />
    </transition>
</template>

<script setup>
import {
    ref
} from "vue";

const props = defineProps(['show']);

const rand = ref(0);

const charactor = () => {
    rand.value = Math.floor(Math.random() * 8);
    console.log(rand.value);
    let src;
    switch (rand.value) {
        case 1:
            src = '2BASA.png';
            break;
        case 2:
            src = 'sasapiyo.png';
            break;
        case 3:
            src = 'gazooo0.png';
            break;
        case 4:
            src = 'shan.png';
            break;
        case 5:
            src = 'hinanu.png';
            break;
        case 6:
            src = 'midodo.png';
            break;
        case 7:
            src = 'yoyomi.png';
            break;
        default:
            src = 'manpuku.png';
            break;
    }

    const url = './images/12th/' + src;
    return url;
    // return new URL(`${url}`, import.meta.url).href;
};
</script>

<style lang="scss" scoped>
.charactor {
    max-height: 200px;
    margin-right: 50px;
    margin-left: 30px;
    transition: all .5s ease;
    opacity: 1;
}

.charactor-enter-from {
    transform: translateX(100px);
    opacity: 0;
}

.charactor-leave-to {
    transform: translateX(-100px);
    opacity: 0;
}

</style>