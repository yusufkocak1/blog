<template>
  <div class="login">
    <Button v-if="!isLogin" v-on:click="login">
      login
    </Button>
    <Button v-else v-on:click="logout">logout</Button>
  </div>
</template>
<script>


export default {
  name: 'login',
  data() {
    return {
      isLogin: false
    }
  },
  components: {},
  methods: {
    login() {

    },
    logout() {

    }
  },
  mounted: function () {

  }
}
</script>
