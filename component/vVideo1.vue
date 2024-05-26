<script>
export default {
  name: 'VideoPlayer',
  data(){
    return{
      startVideo:false
    }
  },
  mounted() {
    this.handleScroll()
    window.addEventListener('scroll', this.handleScroll);
    window.addEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      const {scrollY,scrollX,innerHeight,screenTop} = window
      console.log({scrollY,scrollX,innerHeight,screenTop})

      const videoContainer = this.$refs.video;
      const offsetTop = videoContainer.offsetTop
      console.log(scrollY + (innerHeight / 2), offsetTop)

      if(scrollY + (innerHeight / 2) >  offsetTop){
        console.log('show1')
        // alert(2)
        this.playVideo()
      }
    },
    playVideo() {
      this.startVideo = true
      this.$refs.video.play();
    },
    pauseVideo() {
      this.startVideo = false
      this.$refs.video.pause();
    }
  }
}
</script>
<template>
  <div>
    <div class="video">
      <video ref="video" width="320" height="240" muted loop playsinline>
        <source src="/video/1.mp4" type="video/mp4">
        Your browser does not support the video tag.
      </video>
      <div class="controls">
        <button v-if="!startVideo" @click="playVideo">
          <svg width="16" height="17" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" class="control-centered-small-icon">
            <path class="control-icon-play" d="M5 15.25V4.77a1.44 1.44 0 0 1 1.44-1.62 1.86 1.86 0 0 1 1.11.31l8.53 5c.76.44 1.17.8 1.17 1.51s-.41 1.07-1.17 1.51l-8.53 5a1.86 1.86 0 0 1-1.11.31A1.42 1.42 0 0 1 5 15.25Z"></path>
          </svg>
        </button>
        <button v-else @click="pauseVideo">
          <svg  width="16" height="17" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" class="control-centered-small-icon">
            <g class="control-icon-pause">
              <rect width="4.5" height="14" x="3.75" y="3" rx="1.5"></rect>
              <rect width="4.5" height="14" x="11.75" y="3" rx="1.5"></rect>
            </g>
          </svg>
        </button>
      </div>
    </div>

    <h1 style="text-align: center; margin-top: 20px;">Скрольте вниз</h1>
  </div>
</template>
<style>

.video{
  max-width: 800px;
  height: 450px;
//position: relative;
  margin: 0 auto;

}

.video video{
  width: 100%;
  height: 100%;
}

.controls{
  max-width: 800px;
  height: 450px;
  position: relative;
  z-index: 9;
  display: flex;
  justify-content: flex-end;
  margin-top: -56px;
//margin-right: 20px;
  margin-left: -20px;
//position: absolute;
//bottom: 20px;
//right: 20px;
}
.controls button{

  width: 36px;
  height: 36px;
  border: none;
  background: #F2F2F2;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
}
@media screen and (max-width: 600px) {
  .controls,
  .video{
    height: 200px;
  }
  .controls{
    margin-left: 0;
    margin-right: 20px;
  }
}
</style>