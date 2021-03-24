<template lang="pug">
header.headerHome 
  nav.navHome
    img.logoNetflix(alt="Netflix logo", src="../assets/logo.png")
    router-link(to="/login") Entrar
  main.mainHome
    h1 Filmes, séries e muito mais.
    h2 Sem limites.
    p Assista onde quiser. Cancele quando quiser.
    p Pronto para assistir? Informe seu email para criar ou reiniciar sua assinatura.
    el-form.demo-dynamic(
      :model="dynamicValidateForm",
      ref="dynamicValidateForm",
      label-width="120px"
    )
      el-form-item(
        prop="email",
        :rules="[ { required: true, message: 'Please input email address', trigger: 'blur' }, { type: 'email', message: 'Please input correct email address', trigger: ['blur', 'change'] }, ]"
      )
        el-input(v-model="dynamicValidateForm.email")
      el-form-item
        el-button(type="primary", @click="submitForm('dynamicValidateForm')") Vamos lá &#62;
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
          alert("submit!");
        } else {
          console.log("error submit!!");
          return false;
        }
      });
    },
  },
};
</script>
<style lang="scss">
body {
  background-image: url(../assets/BackgroundHome.png);
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
header.headerHome {
  // -webkit-mask-image: linear-gradient(to bottom, transparent 5%, black 100%);
  background-image: linear-gradient(to top, transparent 20%, black 100%);
  height: 625px;
  nav.navHome {
    display: flex;
    justify-content: space-between;
    img.logoNetflix {
      width: 133px;
    }
  }
  main.mainHome {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    .el-form.demo-dynamic {
      display: flex;
      .el-form-item.is-required {
        .el-form-item__content {
          margin-left: 0;
        }
      }
    }
    .el-form.demo-dynamic {
      display: flex;
      .el-form-item__content {
        margin-left: 0;
      }
    }
  }
}
</style>