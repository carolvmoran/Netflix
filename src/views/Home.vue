<template lang="pug">
.home
  HeaderHome
  BodyHome
</template>

<script>
import HeaderHome from "@/components/HeaderHome.vue";
import BodyHome from "@/components/BodyHome.vue";

export default {
  name: "Home",
  components: {
    HeaderHome,
    BodyHome,
  },
};
</script>
<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
