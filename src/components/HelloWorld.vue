<template>
  <div class="container">
    <h1>{{ msg }}</h1>
    <div class="contact">
      <h2> Contact US </h2>
      <form v-on:submit.prevent="submitForm">

        <div class="form-group">
          <input id="name" v-model="form.name" class="form-control" placeholder="name" type="text">
          <textarea id="message" v-model="form.message" class="form-control" name="message"
                    placeholder="write your letter here..."
                    rows="3"></textarea>
        </div>
        <div class="form-group">

          <div class="button-group">
            <button id="btn">
              <p id="btnText">Send</p>
              <div class="check-box">
                <svg viewBox="0 0 50 50" xmlns="http://www.w3.org/2000/svg">
                  <path d="M14.1 27.2l7.1 7.2 16.7-16.8" fill="transparent"/>
                </svg>
              </div>
            </button>
          </div>
        </div>
      </form>

    </div>
    <p>
      This page is created by <a href="http://github.com/yusufkocak1">yusufkocak1</a>
    </p>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      form: {
        message: '',
        name: ''
      }
    }
  },
  methods: {
    submitForm() {
      const btn = document.querySelector("#btn");
      const btnText = document.querySelector("#btnText");
      if (btnText.innerText === 'X') {
        btnText.innerHTML = "Send";
        btnText.fontSize = "24px";
        btn.style.backgroundColor = "#2f2f2f"
      } else {

        let requestMessage = {
          "fromID": 1,
          "toID": 2,
          "messageText": this.form.name + ' >>> ' + this.form.message
        };
        axios.post('https://yusufkocak-dev-server.herokuapp.com/sendMessage', requestMessage)
            .then((res) => {
              console.log(res)
              btnText.innerHTML = "Thanks";
              btn.classList.add("active");
              btn.disabled = true;
            })
            .catch((error) => {
              btnText.innerHTML = "<b>X<b/>";
              btn.style.backgroundColor = "#D32F2F"
              console.log(error)
            });
      }
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300;400;500;600;700;800;900&display=swap');

h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #fff;
}

.container {
  width: 100%;
  height: 90%;
  padding-top: 3%;
  background-color: #212121;
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
}

.form-group {
  padding: 10px;
  margin: 10px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: start;
}

.form-group input {
  width: 50%
}

.form-control {
  margin: 10px;
  width: 100%;
  padding: 12px 20px;
  box-sizing: border-box;
  border: 2px solid #ccc;
  border-radius: 4px;
  background-color: #f8f8f8;
  font-size: 16px;
  resize: none;
}

.contact {
  width: 50%;
}

button {
  width: 270px;
  height: 80px;
  border: 1px solid #fff;
  outline: none;
  background: #2f2f2f;
  color: #fff;
  font-size: 22px;
  border-radius: 40px;
  text-align: center;
  box-shadow: 0 6px 20px -5px rgba(0, 0, 0, 0.4);
  position: relative;
  overflow: hidden;
  cursor: pointer;
}

.check-box {
  width: 80px;
  height: 80px;
  border-radius: 40px;
  box-shadow: 0 0 12px -2px rgba(0, 0, 0, 0.5);
  position: absolute;
  top: 0;
  right: -40px;
  opacity: 0;
}

.check-box svg {
  width: 40px;
  margin: 20px;
}

svg path {
  stroke-width: 3;
  stroke: #fff;
  stroke-dasharray: 34;
  stroke-dashoffset: 34;
  stroke-linecap: round;
}

.active {
  background: #4CAF50;
  transition: 1s;
}

.active .check-box {
  right: 0;
  opacity: 1;
  transition: 1s;
}

.active p {
  margin-right: 125px;
  transition: 1s;
}

.active svg path {
  stroke-dashoffset: 0;
  transition: 1s;
  transition-delay: 1s;
}

.button-group {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: flex-end;
}
</style>
