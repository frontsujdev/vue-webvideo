<template>
  <video-player class="vjs-custom-skin"
    ref="videoPlayer"
    :options="playerOptions"
    :playsinline="true"
    customEventName="customstatechangedeventname">
  </video-player>
</template>

<script>
import 'videojs-flash'
export default {
  name: 'rtmp-live', //  video 
  props: {
    src: {
      type: String,
      default: 'rtmp://live.hkstv.hk.lxdns.com/live/hks2'
    }
  },
  data () {
    return {
      playerOptions: {
        // height: '320',
        // width: '100%',
        sources: [ {
          type: 'rtmp/mp4',
          src: this.src
        } ],
        techOrder: ['flash'],
        autoplay: true, // 
        // controls: true, // 
        fluid: true, // 
        // preload: 'auto', // 
        // muted: true, // 
        // loop: false, // 
        aspectRatio: "16:9",
        
      }
    }
  }
}
</script>