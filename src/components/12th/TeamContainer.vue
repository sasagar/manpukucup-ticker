<template>
  <transition name="team-container" appear>
    <div class="team-container" v-if="props.show">
      <div class="inner-container">
        <div class="upper">
          <div class="team-futatsuna" :class="props.team.push">
            <span>
              {{ props.team.futatsuna }}
            </span>
          </div>
          <div class="name-container">
            <div class="team-name">
              {{ props.team.name }}
            </div>
            <ul class="team-members">
              <li v-for="member in props.team.members" :key="member.name" >{{ member.name }}</li>
            </ul>
          </div>
        </div>
        <div class="team-msg">
          {{ props.team.message }}
        </div>
      </div>
    </div>
  </transition>
</template>

<script setup>
const props = defineProps(['team','show']);
</script>

<style scoped>
.team-container {
    transition: all .5s ease;
    opacity: 1;
    width: calc(100% - 300px);
    margin-left: 300px;
    z-index: 10;
    display: flex;
    justify-content: center;
    align-items: center;
}

.team-container-enter-from {
    transform: translateX(100px);
    opacity: 0;
}
.team-container-leave-to {
    transform: translateX(-100px);
    opacity: 0;
}

.inner-container {
  display: inline-block;
}

.upper {
  display: flex;
  gap: 20px;
}

.name-container {
  margin-top: 15px;
  flex: 1;
}

.team-futatsuna {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-basis: auto;
  z-index: 10;
}
.team-futatsuna span {
  font-size: 30px;
  line-height: 1;
  transform: rotate(-5deg) translateY(10px);
  background-color: #a5cbff;
  padding: 10px 5px;
}

.team-futatsuna.umi span {
  background-color: #9dc9ff;
}

.team-futatsuna.hanabi span {
  background-color: #1c1c1c;
  color: #fff;
}

.team-futatsuna.bbq span {
  background-color: #92ffc5;
}

.team-name {
  font-family: splatfont;
  font-size: 50px;
  line-height: 1;
}
.team-msg {
  line-height: 1.1;
  font-size: 30px;
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