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
      .boxAboutMovie 
        img.movie(
          src="https://assets.nflxext.com/ffe/siteui/acquisition/ourStory/fuji/desktop/boxshot.png"
        )
        .textMovie
          h4 Stranger Things
          p.download Download em andamento...
        img.load(src="../assets/download-icon.gif")
    .textContainer
      h2 Baixe séries para assistir offline.
      p Salve seus títulos favoritos e sempre tenha algo para assistir.
  .containerBlack
    .textContainer
      h2 Assista quando quiser.
      p Assista no celular, tablet, Smart TV ou notebook sem pagar a mais por isso.
    .imageContainer
      img.tvPhone(
        src="https://assets.nflxext.com/ffe/siteui/acquisition/ourStory/fuji/desktop/device-pile.png",
        alt="imagem de uma tv"
      )
      .tvNetflixPhone
        video(autoplay, playsinline, muted, loop)
          source(
            src="https://assets.nflxext.com/ffe/siteui/acquisition/ourStory/fuji/desktop/video-devices.m4v",
            type="video/mp4"
          )
  .containerBlack
    .textContainerQuestions
      h2 Perguntas frequentes
      el-collapse(v-model="activeName", accordion)
        .collapse(
          v-for="item in dados",
          @click.stop="item.activeIcon = !item.activeIcon",
          :class="[item.activeIcon ? 'girar' : '']"
        )
          i.fas.fa-plus
          el-collapse-item(:title="item.title", :name="item.name")
            div {{ item.text1 }}
            div {{ item.text2 }}
      h3 Pronto para assistir? Informe seu email para criar ou reiniciar sua assinatura.
      el-form.demo-dynamic(
        :model="dynamicValidateForm",
        ref="dynamicValidateForm"
      )
        el-form-item(
          prop="email",
          :rules="[ { required: true, message: 'Por favor, digite um email válido', trigger: 'blur' }, { type: 'email', message: 'Por favor, digite uma Email válido', trigger: ['blur', 'change'] }, ]"
        )
          el-input(v-model="dynamicValidateForm.email", placeholder="Email")
        el-form-item
          el-button(type="primary", @click="submitForm('dynamicValidateForm')") Vamos lá
            span.caracter &#62;
</template>
<script>
export default {
  data() {
    return {
      dynamicValidateForm: {
        email: "",
      },
      activeName: "0",
      dados: [
        {
          title: "O que é a Netflix?",
          name: "1",
          text1:
            "A Netflix é um serviço de transmissão online que oferece uma ampla variedade de séries, filmes e documentários premiados em milhares de aparelhos conectados à internet.",
          text2:
            "Você pode assistir a quantos filmes e séries quiser, quando e onde quiser, sem comerciais – tudo por um preço mensal bem acessível. Aqui você sempre encontra novidades. A cada semana, adicionamos novas séries e filmes.",
          activeIcon: false,
        },
        {
          title: "Quanto custa a Netflix?",
          name: "2",
          text1:
            "Assista à Netflix no seu celular, tablet, Smart TV, notebook ou aparelho de streaming por uma taxa mensal única. Os planos variam de R$21,90 a R$45,90 por mês. Sem contrato nem taxas extras.",
          text2: "",
          activeIcon: false,
        },

        {
          title: "Onde posso assistir?",
          name: "3",
          text1:
            "Assista onde quiser, o quanto quiser e em um número ilimitado de aparelhos. Faça login com sua conta Netflix em netflix.com para começar a assistir no computador ou em qualquer aparelho conectado à Internet compatível com o aplicativo Netflix, como Smart TVs, smartphones, tablets, aparelhos de streaming e videogames.",
          text2:
            "Você também pode baixar a sua série favorita com o aplicativo Netflix para iOS, Android ou Windows 10. Use downloads para levar a Netflix para onde quiser sem precisar de conexão com a Internet. Leve a Netflix com você para qualquer lugar.",
          activeIcon: false,
        },

        {
          title: "Como faço para cancelar?",
          name: "4",
          text1:
            "A Netflix é flexível. Não há contratos nem compromissos. Você pode cancelar a sua conta na internet com apenas dois cliques. Não há taxa de cancelamento – você pode começar ou encerrar a sua assinatura a qualquer momento.",
          text2: "",
          activeIcon: false,
        },
        {
          title: "O que eu posso assistir na Netflix?",
          name: "5",
          text1:
            "A Netflix tem um grande catálogo de filmes, documentários, séries, originais Netflix premiados e muito mais. Assista o quanto quiser, quando quiser.",
          text2: "",
          activeIcon: false,
        },
      ],
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          alert("Email OK, agora clique em Entrar");
        } else {
          console.log("error!!");
          return false;
        }
      });
    },
  },
};
</script>
<style lang="scss">
.bodyHome {
  background-color: black;
  .containerBlack {
    // height: 474px;
    padding: 70px 45px;
    border-top: 8px solid #222222;
    display: flex;
    align-items: center;
    justify-content: center;
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
      position: relative;
      z-index: 0;
      .tv {
        padding-left: 48px;
        width: 530px;
        z-index: 1;
      }
      .tvNetflix {
        position: absolute;
        width: 400px;
        top: 70px;
        margin: 0 auto;
        right: 50px;
        z-index: -1;
        video {
          width: 372px;
        }
      }
      .phone {
        width: 504px;
        margin-right: 96px;
      }
      .boxAboutMovie {
        width: 341px;
        border: 2px solid rgba(255, 255, 255, 0.25);
        border-radius: 0.75em;
        background-color: #000;
        position: absolute;
        display: flex;
        align-items: center;
        justify-content: center;
        bottom: 32px;
        left: 84px;
        padding: 10px;
        .movie {
          width: 52px;
          margin-right: 1em;
        }
        .textMovie {
          text-align: start;
          p.download {
            color: #0071eb;
            font-size: 0.9em;
            font-weight: normal;
          }
        }
        .load {
          width: 3em;
          margin-left: 1em;
        }
      }
      .tvPhone {
        width: 555px;
      }
      .tvNetflixPhone {
        position: absolute;
        width: 400px;
        top: 41px;
        margin: 0 auto;
        right: 80px;
        z-index: -1;
        video {
          width: 338px;
        }
      }
    }
    .textContainerQuestions {
      display: flex;
      align-items: center;
      width: 70%;
      flex-direction: column;
      h2 {
        font-size: 50px;
      }
      .el-collapse {
        margin-top: 4em;
        .collapse {
          position: relative;
          transition-duration: 0.5s;
          i.fas.fa-plus {
            position: absolute;
            margin: 0 auto;
            top: 26px;
            right: 25px;
            font-size: 27px;
          }
          &.girar {
            i.fas.fa-plus {
              transform: rotate(+45deg);
            }
          }
          .el-collapse-item {
            width: 815px;
            // padding: 20px;
            background-color: #303030;
            margin-bottom: 8px;
            text-align: start;
            font-size: 1.6rem;
            .el-collapse-item__header {
              padding: 25px;
              outline: none;
            }
            .el-collapse-item__content {
              // padding-top: 1.2em;
              margin-top: 10px;
            }
          }
          .el-collapse-item.is-active {
            .el-collapse-item__header.is-active {
              border-bottom: 2px solid #000;
            }
            .el-collapse-item__wrap {
              padding: 25px;
              .el-collapse-item__content {
                div {
                  margin-bottom: 20px;
                }
              }
            }
          }
        }
      }
      h3 {
        font-size: 19px;
        margin: 20px;
        font-weight: normal;
      }
      .el-form.demo-dynamic {
        display: flex;
        .el-form-item.is-required {
          .el-form-item__content {
            margin-left: 0;
            .el-input__inner {
              width: 450px;
              height: 60px;
              padding: 10px;
              outline: none;
              border-radius: 3px;
              border: solid 1px #8c8c8c;
              border-bottom-right-radius: 0;
              border-top-right-radius: 0;
              &::placeholder {
                color: #8c8c8c;
                font-size: 16px;
              }
            }
          }
        }
        .el-form-item {
          display: flex;
          .el-form-item__content {
            margin-left: 0;
            .el-button.el-button--primary {
              width: 186px;
              height: 60px;
              font-size: 26px;
              font-weight: 600;
              padding: 0 26px;
              outline: none;
              color: white;
              border: 0;
              border-left: 1px solid #333;
              border-bottom-left-radius: 0;
              border-top-left-radius: 0;
              border-radius: 2px;
              background-color: #e50914;
              span.caracter {
                font-weight: normal;
                margin-left: 5px;
              }
            }
          }
        }
      }
    }
  }
}
</style>