<template>
  <div id="app">
    <h1>Welcom to Cloud Webpage</h1>
    <span>Please Upload File</span>
    <br>
    <br>
    <input type="file" accept="image/*" @change="uploadImage($event)" id="file-input" />
    <span>{{result}}</span>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: "app",
  components: {},
  data() {
    return {
      result: null
    }
  },
  methods: {
    uploadImage(event) {
      const URL = "http://localhost:5000/upload";

      let data = new FormData();
      data.append("name", "my-picture");
      data.append("file", event.target.files[0]);

      let config = {
        header: {
          "Content-Type": "image/png"
        }
      };

      axios.put(URL, data, config).then(response => {
        console.log(response)
      });
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
