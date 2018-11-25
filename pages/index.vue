<template>
  <section class="container">
    <div>
      <logo/>
      <input type="email" placeholder="Enter Your Email"><button>Get Beta Access</button>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  }
}
</script>

<style lang="scss">
@import url('~/assets/styles.scss');
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>
