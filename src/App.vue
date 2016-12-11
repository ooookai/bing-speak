<template>
  <div id="app">
    <img id="logo" src="./assets/logo.png">
    <h1>{{ msg }}</h1>
    <x-audio :audio-src="audioSrc"></x-audio>
    <select v-model="locale">
      <option v-for="option in select.locale" v-bind:value="option">
        {{ option }}
      </option>
    </select>
    <select v-model="gender">
      <option v-for="option in select.gender" v-bind:value="option">
        {{ option }}
      </option>
    </select>
    <!-- <a :href="audioSrc" download>Download</a> -->
    <a :href="audioSrc" target="_blank" download="audio">Download</a>
    <p></p>
    <textarea v-model="text" style="width:500px;height:100px;"></textarea>
  </div>
</template>
<script>
import xAudio from './x-audio.vue'

export default {
  name: 'app',
  data() {
    return {
      msg: 'Test & Download Microsoft Bing Translator Speak',
      translatorUrl: 'http://www.bing.com/translator/api/language/Speak?',
      locale: 'zh-CN',
      gender: 'Male',
      media: 'audio/mp3',
      text: '測試',
      select: {
        locale: ['zh-CN', "zh-HK", "zh-TW", "en-US", "en-AU", "en-CA", "en-GB", "en-IN"],
        gender: ['Male', 'Female'],
      }
    }
  },
  computed: {
    audioSrc() {
      return this.translatorUrl + 'locale=' + this.locale + '&' + 'gender=' + this.gender + '&' + 'media=' + this.media + '&' + 'text=' + this.text;
    },
  },
  components: {
    'x-audio': xAudio,
  },

}
</script>
<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#logo {
  max-height: 100px;
}

h1,
h2 {
  font-weight: normal;
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
  color: #42b983;
}

input {
  display: inline;
}

x-audio {
  display: inline;
}
</style>
