<template>
  <section class="container">
    <div>
      <logo/>
      <input
        v-validate="'required|email'"
        v-on:keydown.enter="submitForm"
        type="email"
        placeholder="Enter Your Email"
        v-model="email"
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
  data: function() {
    return {
      email: null,
      emailSent: false
    }
  },
  methods: {
    submitForm() {
      let vm = this
      this.$validator.validate().then(result => {
        if (!result) {
        } else {
          this.$axios({
            method: 'post',
            url:
              'https://us-central1-dancengine-221904.cloudfunctions.net/subscribe',
            headers: { 'Content-Type': 'application/json' },
            data: vm.email
          }).then(res => {
            console.log(res.data)
          })
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
