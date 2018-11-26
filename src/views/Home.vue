<template>
  <div class="about">
    <div class="wrapper">
      <input type="text" placeholder="Enter your server URL" v-model="serverURL">
      <input type="text" placeholder="Enter your access PW" v-model="accessPW">
      <input type="submit" value="View" @click="populateList()">
    </div>
    <div style="margin-bottom: 70px;">
      <p v-for='item in list' :key='item.id'>{{item.email}}</p>    </div>
    <div style="color: white; background-color: black; position: fixed; bottom: 50px; width: 100%; height: 20px;">
      <p>Total: {{list.length}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'list',
  data(){
    return {
      list: [],
      serverURL: '',
      accessPW: '',
    };
  },
  methods: {
    populateList(){
      fetch(`${this.serverURL}/view`, {
        method: 'POST',
        body: JSON.stringify({ password: this.accessPW }),
        headers: {'Content-Type': 'application/json'},
      })
        .then(res => res.json())
        .then((data) => {
          this.list = data;
        })
        .catch(err => console.log(err));
    },
  },
}
</script>

<style scoped>
.wrapper {
  background-color: black; display: flex; padding: 10px; justify-content: space-around; flex-wrap: wrap;
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
input[type=submit] {
  cursor: pointer;
  padding: 10px 30px;
}
@media only screen and (max-width: 600px) {
    .wrapper {
        flex-direction: column;
    }
}
</style>
