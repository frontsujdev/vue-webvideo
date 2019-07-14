<template>
  <video-player class="vjs-custom-skin"
    ref="videoPlayer"
    :options="playerOptions"
    @ready="playerReadied">
  </video-player>
</template>

<script>
import 'videojs-contrib-hls'

export default {
  name: 'hls-live', //  video 
  props: {
    src: {
      type: String,
      default: 'http://gcqq450f71eywn6bv7u.exp.bcevod.com/mda-hiup6h1qdymgf3fe/mda-hiup6h1qdymgf3fe.m3u8'
    }
  },
  data () {
    return {
      playerOptions: {
        // height: '320',
        // width: '100%',
        sources: [{
          withCredentials: false,
          type: "application/x-mpegURL",
          src: this.src
        }],
        controlBar: {
          timeDivider: false,
          durationDisplay: false
        },
        flash: { hls: { withCredentials: false }},
        html5: { hls: { withCredentials: false }},
        autoplay: true, // 
        // controls: true, // 
        fluid: true, // 
        aspectRatio: "16:9",
      }
    }
  },
  methods: {
    playerReadied(player) {
      var hls = player.tech({ IWillNotUseThisInPlugins: true }).hls
      player.tech_.hls.xhr.beforeRequest = function(options) {
        // console.log(options)
        return options
      }
    }
  }
}
</script>