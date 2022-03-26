<template>
  <div>
    <ul>
      <li v-for="item in messages" :key="item">{{item}}</li>
    </ul>
  </div>
</template>
<script>
import axios from "axios";

export default {
  name: 'ShowLetter',
  data() {
    return {
      messages: []
    }
  },
  created: function () {
        let requestMessage = {
          "fromID": 1,
          "toID": 2
        };
        axios.post('https://yusufkocak-dev-server.herokuapp.com/getMessage', requestMessage)
            .then((res) => {
              console.log(res)
              this.messages = res.data;
            })
            .catch((error) => {
              console.log(error)
            });
      }


}
</script>
<style>
ul{
  background-color:#fff;
  color:#000;
}
li{
  margin:8px;
  list-style: none
}

</style>