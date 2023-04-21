<template>
  <transition name="team-container" appear>
    <div  class="team-container">
      <div class="inner-container">
        <div class="upper">
          <div class="team-futatsuna">
            <span>
              {{ props.team.futatsuna }}
            </span>
          </div>
          <div class="name-container">
            <div class="team-name">
              {{ props.team.team }}
            </div>
            <ul class="team-members">
              <li v-for="member in props.team.members" :key="member.name" >{{ member.name }}</li>
            </ul>
          </div>
        </div>
        <div class="team-msg">
          {{ props.team.msg }}
        </div>
      </div>
    </div>
  </transition>
</template>

<script setup>
import { defineProps } from 'vue';
const props = defineProps(['team']);
</script>

<style scoped>
.inner-container {
  display: inline-block;
  /* margin: auto; */
  /* margin-left: 300px; */
  /* position: relative; */
}

.upper {
  display: flex;
  gap: 20px;
}

.name-container {
  /* display: flex; */
  /* align-items: flex-start; */
  margin-top: 15px;
  /* position: relative; */
  flex: 1;
}

.team-futatsuna {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-basis: auto;
  /* position: absolute; */
  /* top: 20px;
  left: 0; */
  z-index: 10;
}
.team-futatsuna span {
  font-size: 40px;
  line-height: 1;
  transform: rotate(-5deg) translateY(10px);
  background-color: #ffa5cb;
  padding: 10px 5px;
}
.team-name {
  font-family: splatfont;
  font-size: 50px;
  line-height: 1;
  /* margin-left: 400px; */
  /* position: absolute; */
  /* top: 10px; */
  /* left: 300px; */
}
.team-msg {
  line-height: 1.2;
  font-size: 35px;
  margin-top: 10px;
  max-width: 100%;
  text-align: center;
  padding-top: 10px;
  border-top: solid 1px #ffffff99;
}

.team-members {
  font-size: 32px;
  list-style-type: none;
  display: flex;
  align-items: center;
  margin: 10px 0 0;
  padding: 0;
}

.team-members::before {
  display: block;
  content: 'メンバー:';
  font-size: 35px;
  font-family: splatfont;
  line-height: 1;
  margin-right: 10px;
}

.team-members li {
  /* font-size: 35px; */
  line-height: 1;
}

.team-members li + li {
  margin-left: 10px;
}

.team-members li + li::before {
  display: inline;
  content: '・';
  margin-right: 10px;
}
</style>