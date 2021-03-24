<template lang="pug">
.home
  HeaderHome
</template>

<script>
import HeaderHome from "@/components/HeaderHome.vue";

export default {
  name: "Home",
  components: {
    HeaderHome,
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
