<template lang="pug">
header.headerHome 
  nav.navHome
    .navBar
      img.logoNetflix(alt="Netflix logo", src="../assets/logo.png")
      .buttons
        .btnLang 
          i.fas.fa-globe 
          .lang Português
          i.fas.fa-caret-down
        router-link.btnLogin(to="/login") Entrar
  main.mainHome
    h1 Filmes, séries e muito mais.
    h2 Sem limites.
    p Assista onde quiser. Cancele quando quiser.
    h3 Pronto para assistir? Informe seu email para criar ou reiniciar sua assinatura.
    el-form.demo-dynamic(
      :model="dynamicValidateForm",
      ref="dynamicValidateForm",
      label-width="120px"
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
body {
  background-image: url(../assets/BackgroundHome.jpg);
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
header.headerHome {
  // background-image: linear-gradient(to bottom, black 90%, transparent 10%);
  background: rgb(0, 0, 0, 0.4);
  background-image: linear-gradient(
    to top,
    rgba(0, 0, 0, 0.8) 0,
    rgba(0, 0, 0, 0) 60%,
    rgba(0, 0, 0, 0.8) 100%
  );
  width: 100%;
  height: 625px;
  display: flex;
  flex-direction: column;
  align-items: center;
  nav.navHome {
    width: 1349px;
    height: 84px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    .navBar {
      width: 1237px;
      height: 48px;
      margin: 0 56px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      img.logoNetflix {
        width: 133px;
      }
      .buttons {
        display: flex;
        .btnLang {
          width: 120px;
          height: 36px;
          margin: 0 30px;
          font-size: 0.9rem;
          border: 1px solid white;
          border-radius: 3px;
          display: flex;
          align-items: center;
          justify-content: center;
          .lang {
            font-weight: 400;
            margin: 0 5px;
          }
        }
        .btnLogin {
          width: 79px;
          height: 34px;
          font-size: 1rem;
          font-weight: 400;
          color: white;
          text-decoration: none;
          border-radius: 3px;
          background-color: #e50914;
          display: flex;
          align-items: center;
          justify-content: center;
        }
      }
    }
  }
  main.mainHome {
    width: 950px;
    height: 467px;
    padding: 75px 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-end;
    h1 {
      font-size: 50px;
    }
    h2 {
      font-size: 50px;
    }
    h3 {
      font-size: 19px;
      margin: 20px;
      font-weight: normal;
    }
    p {
      font-size: 26px;
      margin: 16px 0;
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
          margin-left: 0 !important;
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
</style>