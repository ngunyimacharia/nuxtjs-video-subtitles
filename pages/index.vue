<template>
  <cld-video :publicId="video" controls="true" autoplay="true" >
    <cld-transformation :overlay="{publicId: subtitle, resourceType: 'subtitles'}" />
    <cld-transformation flags="layer_apply" />
  </cld-video>
</template>

<script>
export default {
  data(){
    return {
      video:"nuxtjs-video-subtitles/video",
      subtitle:"nuxtjs-video-subtitles/subtitles.srt",
    }
  }
}
</script>
