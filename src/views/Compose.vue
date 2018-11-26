<template>
  <div class="about">
    <div class="wrapper" v-if="!test && !send">
      <input type="button" value="Test" @click='test = !test'>
      <input type="button" value="Send" @click='send = !send'>
    </div>
    <div class="wrapper" v-if="test">
      <input type="button" value="Back" @click='test = !test'>
      <input type="text" placeholder="List of email addresses">
      <input type="text" placeholder="Enter your server URL" v-model="serverURL">
      <input type="text" placeholder="Enter your access PW" v-model="accessPW">
      <input type="button" value="Send Test Email" @click='test()'>
    </div>
    <div class="wrapper" v-if="send">
      <input type="button" value="Back" @click='send = !send'>
      <input type="text" placeholder="Enter your server URL" v-model="serverURL">
      <input type="text" placeholder="Enter your access PW" v-model="accessPW">
      <input type="button" value="Send Email to Mailing List" @click='send()'>
    </div>
    <div style="display: flex; justify-content: center; margin-top: 20px;">
      <textarea name="message" style="width: 80%; height: 350px; resize:none;"></textarea>
    </div>
  </div>
</template>

<script>
export default {
  name: 'compose',
  data(){
    return {
      serverURL: '',
      accessPW: '',
      test: false,
      send: false,
    }
  }
}
</script>

<style scoped>
.wrapper {
  background-color: black;
  display: flex;
  padding: 10px;
  justify-content: space-around;
  flex-wrap: wrap;
}
input {
  padding: 10px;
  margin: 10px;
  background-color: black;
  color: white;
  outline: none;
  border: 2px solid #42b983;
  border-radius: 5px;
}
input[type=button] {
  cursor: pointer;
  padding: 10px 30px;
}
@media only screen and (max-width: 1000px) {
    .wrapper {
        flex-direction: column;
    }
}
</style>
