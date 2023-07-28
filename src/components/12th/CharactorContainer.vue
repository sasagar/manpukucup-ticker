<template>
    <Transition name="charactor" appear>
        <div class="charactor-container" v-if="props.show">
            <div class="charactor-inner">
                <span>{{ char }}</span>
                <img :src="charactor()" alt="キャラクター" class="charactor" />
            </div>
            <div class="charactor-inner">
                <img :src="charactor2()" alt="キャラクター" class="charactor" />
                <span>{{ char2 }}</span>
            </div>
        </div>
    </Transition>
</template>

<script setup>
import {
TransitionGroup,
    computed,
    ref
} from "vue";

const props = defineProps(['show']);

const rand = ref(0);
const rand2 = ref(0);

const charName = [
    'まんぷく',
    '2BASA',
    'ささぴよ',
    'がずにゃん',
    'しゃん',
    'ひなぬー',
    'みどど',
    'よよみ',
]

const charactor = () => {
    rand.value = Math.floor(Math.random() * 8);
    console.log(rand.value);

    return returnSrc(rand.value);
};

const charactor2 = () => {
    rand2.value = Math.floor(Math.random() * 8);
    while (rand2.value == rand.value) {
        rand2.value = Math.floor(Math.random() * 8);
    }
    console.log(rand2.value);

    return returnSrc(rand2.value);
};

const char = computed(() => {
    return charName[rand.value];
});

const char2 = computed(() => {
    return charName[rand2.value];
});

const returnSrc = (val) => {
    let src;
    let char;
    switch (val) {
        case 1:
            src = '2BASA.png';
            char = '2BASA';
            break;
        case 2:
            src = 'sasapiyo.png';
            char = 'ささぴよ'
            break;
        case 3:
            src = 'gazooo0.png';
            char = 'がずにゃん';
            break;
        case 4:
            src = 'shan.png';
            char = 'しゃん';
            break;
        case 5:
            src = 'hinanu.png';
            char = 'ひなぬー';
            break;
        case 6:
            src = 'midodo.png';
            char = 'みどど';
            break;
        case 7:
            src = 'yoyomi.png';
            char = 'よよみ';
            break;
        default:
            src = 'manpuku.png';
            char = 'まんぷく'
            break;
    }

    const url = './images/12th/' + src;
    return url;
}
</script>

<style lang="scss" scoped>
.charactor-container {
    position: absolute;
    bottom: 200px;
    right: 0;
    width: 355px;
    height: 680px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    transition: all .5s ease;
    opacity: 1;
    row-gap: 30px;
}

.charactor-inner {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    span {
        font-family: splatfont;
        color: rgba(0, 0, 0, .7);
        line-height: 1;
    }
}

.charactor {
    max-height: 200px;
    margin-right: 50px;
    margin-left: 30px;
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