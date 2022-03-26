<template>
  <div class="about">

    <ShowLetter v-if="isLogin"></ShowLetter>
    <p v-else v-on:click="secret">Dutluk</p>
  </div>
</template>
<script>
import ShowLetter from '@/components/ShowLetter';


export default {
  name: 'about',
  data() {
    return {
      isLogin: false,
      temp: 0
    }
  },
  components: {
    ShowLetter
  },
  methods: {
    secret() {
      if (this.temp > 7) {
        this.isLogin = true;
      } else {
        this.temp++;
      }

    }
  },
  created: function () {

  }
}
</script>
