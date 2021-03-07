<template>
  <div class="home">
    <Nav />
    <Info  />
  </div>
</template>

<script>
import Nav from "@/components/navigation_bar.vue";
import Info from "@/components/information.vue";


export default {
  name: "Home",
  components: {
    Nav,
    Info,
  },
  
};
</script>
<style scoped>
</style>
