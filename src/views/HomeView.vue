<script setup>
import {useTemplateRef} from "vue";

const gameFrame = useTemplateRef('gameFrame')
let interval

function startScrollLeft() {
  interval = setInterval(() => {
    gameFrame.value.scrollBy(-100, 0)
  }, 10)
}
function startScrollRight() {
  interval = setInterval(() => {
    gameFrame.value.scrollBy(+100, 0)
  }, 10)
}
function stopScrolling() { clearInterval(interval) }
</script>

<template>
  <main>
    <div class="top-hud"></div>
    <div class="frame">
      <div @mouseover="startScrollLeft" @mouseout="stopScrolling" class="scroll-left"></div>
      <div @mouseover="startScrollRight" @mouseout="stopScrolling" class="scroll-right"></div>

      <div ref="gameFrame" id="game-frame">
        <div id="main-area">
          <div id="player-base"></div>
          <div id="enemy-base"></div>
        </div>
      </div>
    </div>
        <div class="floor"></div>
  </main>
</template>

<style>
main {
  display: flex;
  flex-direction: column;
  width: 100vw;
  height: 100vh;
  margin: 0;
}
.top-hud {
  height: 100px;
}
.frame {
  position: relative;
  height: 100%;
}
#game-frame {
  height: 100%;
  width: 100%;
  overflow-x: scroll;
}
#main-area {
  height: 100%;
  width: 10000px;
  background: linear-gradient(90deg, #e66465, #9198e5);

}
.scroll-left, .scroll-right {
  position: absolute;
  height: 100%;
  width: 100px;
  background: aquamarine;
}
.scroll-right {
  right: 0;
}
.floor {
  width: 100%;
  height: 50px;
  top: 0;
  background: green;

}
</style>
