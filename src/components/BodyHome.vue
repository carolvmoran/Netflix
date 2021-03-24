<template lang="pug">
.bodyHome
  .containerBlack
    .textContainer
      h2 Aproveite na TV.
      p Assista em Smart TVs, PlayStation, Xbox, Chromecast, Apple TV, aparelhos de Blu-ray e outros dispositivos.
    .imageContainer
      img.tv(src="../assets/tv.png", alt="imagem de uma tv")
      .tvNetflix
        video(autoplay, playsinline, muted, loop)
          source(
            src="https://assets.nflxext.com/ffe/siteui/acquisition/ourStory/fuji/desktop/video-tv-0819.m4v",
            type="video/mp4"
          )
  .containerBlack
    .imageContainer
      img.phone(
        src="https://assets.nflxext.com/ffe/siteui/acquisition/ourStory/fuji/desktop/mobile-0819.jpg",
        alt="imagem de celular"
      )
    .textContainer
      h2 Baixe séries para assistir offline.
      p Salve seus títulos favoritos e sempre tenha algo para assistir.
</template>
<script>
export default {};
</script>
<style lang="scss">
.bodyHome {
  background-color: black;
  .containerBlack {
    height: 474px;
    padding: 70px 45px;
    border-top: 8px solid #222222;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    .textContainer {
      width: 595px;
      height: 174px;
      //   padding-right: 48px;
      text-align: start;
      h2 {
        font-size: 50px;
      }
      p {
        font-size: 26px;
        margin-top: 20px;
      }
    }
    .imageContainer {
      .tv {
        padding-left: 48px;
        width: 530px;
        z-index: 100;
        position: relative;
      }
      .tvNetflix {
        position: absolute;
        width: 430px;
        top: 110px;
        margin: 0 auto;
        right: 160px;
        z-index: 0;
        video {
          width: 400px;
        }
      }
      .phone {
        width: 504px;
        margin-right: 96px;
      }
    }
  }
}
</style>