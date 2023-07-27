<template>
  <TickerContainer />
</template>

<script>
import TickerContainer from './components/12th/TickerContainer.vue'
// import Test from './components/Test.vue'

export default {
  name: 'App',
  components: {
    TickerContainer,
    // Test
  }
}
</script>

<style>
@font-face {
  font-family: "splatfont";
  src: url(/font/Splatoon1-common.3b7ce8b3c19f74921f51.woff2) format("woff2");
  font-weight: normal;
  font-style: normal;
}
@font-face {
  font-family: "splatfont";
  src: url(/font/Splatoon1-symbol-common.38ddb9a11cb1f225e092.woff2)
    format("woff2");
  font-weight: normal;
  font-style: normal;
}
@font-face {
  font-family: "splatfont";
  src: url(/font/Splatoon1-cjk-common.62441e2d3263b7141ca0.woff2)
    format("woff2");
  font-weight: normal;
  font-style: normal;
}
@font-face {
  font-family: "splatfont";
  src: url(/font/Splatoon1JP-hiragana-katakana.7650dccc9af86f19f094.woff2)
    format("woff2");
  font-weight: normal;
  font-style: normal;
}
@font-face {
  font-family: "splatfont";
  src: url(/font/Splatoon1JP-level1.fafc97f04a568e26ba52.woff2)
    format("woff2");
  font-weight: normal;
  font-style: normal;
}
@font-face {
  font-family: "splatfont";
  src: url(/font/Splatoon1JP-level2.225bb1db5962c9d61773.woff2)
    format("woff2");
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: "splatfont";
  src: url(/font/Splatfont.ttf) format("truetype");
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: "splatfont2";
  src: url(/font/Splatoon2-common.4e7b2cad208fa2fc42ca.woff2) format("woff2");
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: "splatfont2";
  src: url(/font/Splatoon2-cjk-common.7dc791c403ed7f33d73e.woff2)
    format("woff2");
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: "splatfont2";
  src: url(/font/Splatoon2JP-hiragana-katakana.f423b5ce60b7456df1b3.woff2)
    format("woff2");
  font-weight: normal;
  font-style: normal;
}
@font-face {
  font-family: "splatfont2";
  src: url(/font/Splatoon2JP-level1.1f43f499aa71ee002067.woff2)
    format("woff2");
  font-weight: normal;
  font-style: normal;
}
@font-face {
  font-family: "splatfont2";
  src: url(/font/Splatoon2JP-level2.9742567c70e359573d6d.woff2)
    format("woff2");
  font-weight: normal;
  font-style: normal;
}
@font-face {
  font-family: "splatfont2";
  src: url(/font/Splatfont2.ttf) format("truetype");
  font-weight: normal;
  font-style: normal;
}

body {
  margin: 0;
  padding: 0;
}
#app {
  width: 1920px;
  height: 1080px;
  /* background-color: #00FF00; */
  font-family: splatfont2;
  font-size: 50px;
  position: relative;
}
</style>
