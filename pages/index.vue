<template>
  <Tutorial/>
</template>

<script>

const { default: srtParser2 } = require("srt-parser-2");

export default {
  data(){
    return {
      subtitleFile: "https://res.cloudinary.com/hackit-africa/raw/upload/v1647426873/nuxtjs-video-subtitles/subtitles.srt",
      subtitlesArray: null
    }
  },
  async mounted(){
    const srtData = await this.readSubtitleFile();
    this.parseSrtData(srtData);
  },
  methods:{
    readSubtitleFile(){
      return new Promise(async (resolve, reject) => {
        const blob = await (await fetch(this.subtitleFile)).blob();
        const reader = new FileReader();
        reader.readAsText(blob);
        reader.addEventListener(
          'load', 
          (e) => resolve(e.target.result)
        );
      });
    },
    parseSrtData(srtData){
      var parser = new srtParser2()
      this.subtitlesArray =  parser.fromSrt(srtData);
      console.log(this.subtitlesArray);
    }
  }
}
</script>
