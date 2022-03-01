<template>
  <main>

    <section class="input-section">
      <div class="container">
        <h2>Create your awesome Memes !</h2>
        <label>Select an image :</label>
        <input type="file" ref="file" @change="handleFile" accept="image/*">
        <label>Top Text :</label>
        <input type="text" v-model="meme.topText" placeholder="Enter top text here" >
        <label>Bottom Text :</label>
        <input type="text" v-model="meme.bottomText" placeholder="Enter bottom text here" >
      </div>
    </section>
    <section class="meme-section">
      <div ref="memeElement" class="container">
        <h2 v-if="meme.topText" class="top-text">{{ meme.topText }}</h2>
        <div class="meme-img">
          <img :src="meme.imgURL" alt="">
        </div>
        <h2 v-if="meme.bottomText" class="bottom-text">{{ meme.bottomText }}</h2>
      </div>
    </section>

    <section class="action-section">
      <div class="container">
        <h3>{{ memeMsg }}</h3>
        <a v-show="!generated" @click="handleGenerate" class="btn btn-generate">Generate</a>
        <a v-show="generated" class="btn btn-download" ref="downloadBtn">Download</a>
        <a @click="handleReset" class="btn-reset">Reset</a>
      </div>
    </section>

  </main>
</template>

<script setup>
import { reactive, ref } from "@vue/reactivity"
import html2canvas from 'html2canvas'

const memeElement = ref(null)
const file = ref(null)
const downloadBtn = ref(null)
const generated = ref(false)
const memeMsg = ref('Please select an image to continue.')

const meme = reactive({
  topText: '',
  bottomText: '',
  imgURL: ''
})

const handleFile = (e) => {
  generated.value = false
  let file = URL.createObjectURL(e.target.files[0])
  meme.imgURL = file
  memeMsg.value = 'Now, generate your meme.'
}
const handleGenerate = () => {
  if (meme.imgURL) {
    html2canvas(memeElement.value)
    .then((canvas) => {
      var img = canvas.toDataURL("image/jpeg")
      downloadBtn.value.download = 'my-meme.jpg'
      downloadBtn.value.href = img
      generated.value = true
      memeMsg.value = 'Finally, download your meme!'
    })
  }
}
const handleReset = () => {
  file.value.value = ''
  meme.topText = ''
  meme.imgURL = ''
  meme.bottomText = ''
  generated.value = false
  memeMsg.value = 'Please select an image to continue.'
}
</script>

<style>
.input-section {
  padding: 4rem 0 1rem;
}
.input-section h2 {
  text-align: center;
  margin-bottom: 2rem;
}
label {
  display: block;
  font-size: .875rem;
  margin-bottom: .25rem;
}
input {
  width: 100%;
  padding: .5rem 1rem;
  border: 1px solid #004f99;
  border-radius: .25rem;
  outline: none;
  background-color: #003566;
  color: #dbdbdb;
  margin-bottom: .75rem;
}
input[type="file"] {
  cursor: pointer;
}
.meme-section {
  text-align: center;
}
.meme-img {
  background: #666;
  min-height: 300px;
  display: flex;
}
.top-text {
  background-color: #E5FF00;
  color: #000;
}
.bottom-text {
  margin-top: -7px;
  background-color: #000;
  color: #FFF;
}
.top-text,
.bottom-text {
  font-family: sans-serif;
  font-size: 1rem;
  font-weight: 600;
  line-height: 1.3;
  padding: .625rem .5rem;
  margin: auto;
  min-height: 2rem;
}
.action-section {
  padding: 1.5rem 0 4rem;
  text-align: center;
}
.action-section h3 {
  font-size: 1.125rem;
  margin-bottom: .75rem;
}
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  padding: .5rem 1rem;
  width: 100%;
  font-weight: 500;
  transition: .3s;
  font-size: 1rem;
  border-radius: .125rem;
}
.btn-generate {
  background-color: #0069cc;
  color: #FFF;
}
.btn-generate:hover {
  background-color: #0077e6;
  color: #FFF;
}
.btn-download {
  background-color: #00b300;
  color: #FFF;
}
.btn-download:hover {
  background-color: #00cc00;
  color: #FFF;
}
.btn-reset {
  display: inline-flex;
  margin-top: 16px;
  cursor: pointer;
}

@media screen and (min-width: 420px) {
  .top-text,
  .bottom-text {
    font-size: 1.125rem;
  } 
}
@media screen and (min-width: 480px) {
  .top-text,
  .bottom-text {
    font-size: 1.25rem;
  } 
}
</style>