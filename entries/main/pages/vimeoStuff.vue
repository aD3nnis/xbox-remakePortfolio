<template lang="pug">
.video-container_box
  .box_video
    client-only
      vue-vimeo-player.testing( ref="player" :video-id="videoID"  :options="options" :player-height="height" :player-width="width")
    //-  <div class="main-tool"></div>    //  v-bind
    //-    <div class="scrollable"></div>
</template>
<script>
import { vueVimeoPlayer } from 'vue-vimeo-player'

export default {
  components: { vueVimeoPlayer },
  data () {
    return {
      width: '500px',
      videoID: '783455878',
      options: {
        muted: true,
        autoplay: true
      }
    }
  }
}
</script>
<style>
.video-container_box {
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: aquamarine;
  position: relative;
}
.box_video{
  position: relative;/* 16:9 aspect ratio (change this value to match your video's aspect ratio) */
  height: 80%;
  width: 80%;
  background-color: bisque;
}
.box_video .testing {
  /* position: absolute; */
  /* display: flex; */
  width: 100%;
  height: 100%;
}
.box_video iframe {
  width: 100%;
  height: 100%;
}
</style>
