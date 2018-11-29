<template>
  <section class="container">
    <div>
      <logo/>
      <input
        v-validate="'required|email'"
        v-on:keydown.enter="submitForm"
        type="email"
        placeholder="Enter Your Email"
      >
      <button @click="submitForm">Get Beta Access</button>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  },
  methods: {
    submitForm() {
      this.$validator.validate().then(result => {
        if (!result) {
          alert('not valid')
        } else {
          alert('valid')
        }
      })
    }
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
  position: relative;
}
.container div {
  z-index: 99;
}
.container::after {
  content: '';
  background: url('/background.jpg');
  background-size: cover;
  width: 100vw;
  height: 100vh;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 10;
  filter: saturate(0);
  opacity: 0.1;
}
</style>
