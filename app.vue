<script>
import {defineComponent} from "vue";
import VideoPlayer from "~/component/vVideo1.vue";
import VideoPlayer2 from "~/component/vVideo2.vue";

export default defineComponent({
  components: {VideoPlayer2, VideoPlayer}
})
</script>
<template>
 <video-player />
 <video-player2 />
</template>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
}
</style>
