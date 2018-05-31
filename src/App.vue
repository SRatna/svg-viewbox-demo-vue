<template>
  <div id="app">
    <h3>SVG View-Box Demo</h3>
    <span class="note">
      SVG: (width, height) = (100, 100)
    </span>
    <span class="note">
      Circle: (x, y) = (50, 50) & r = 50
    </span>
    <br>
    <div class="svg">
      <svg height="100" width="100" :viewBox="getViewBox">
        <circle cx="50" cy="50" r="50" fill="red" />
      </svg>
    </div>
    <br>
    <br>
    <h3>
      ViewBox Parameters
    </h3>
    <div>
      <span>Min X ({{minX}})</span>
      <button @click="minX >= -100 ? minX = minX * 1 - 1 : minX = -100">&minus;</button>
      <button @click="minX < 100 ? minX = minX * 1 + 1 : minX = 100">+</button>
      <button @click="minX = 0">R</button>
      <br>
      <input type="range" min="-100" max="100" v-model="minX">
    </div>
    <div>
      <span>Min Y ({{minY}})</span>
      <button @click="minY >= -100 ? minY = minY * 1 - 1 : minY = -100">&minus;</button>
      <button @click="minY < 100 ? minY = minY * 1 + 1 : minY = 100">+</button>
      <button @click="minY = 0">R</button>
      <br>
      <input type="range" min="-100" max="100" v-model="minY">
    </div>
    <div>
      <span>Width ({{width}})</span>
      <button @click="width > 1 ? width = width * 1 - 1 : width = 1">&minus;</button>
      <button @click="width < 1000 ? width = width * 1 + 1 : width = 1000">+</button>
      <button @click="width = 100">R</button>
      <br>
      <input type="range" min="1" max="1000" v-model="width">
    </div>
    <div>
      <span>Height ({{height}})</span>
      <button @click="height > 1 ? height = height * 1 - 1 : height = 1">&minus;</button>
      <button @click="height < 1000 ? height = height * 1 + 1 : height = 1000">+</button>
      <button @click="height = 100">R</button>
      <br>
      <input type="range" min="1" max="1000" v-model="height">
    </div>
  </div>
</template>

<script>

  export default {
    name: 'app',
    data: function () {
      return {
        minX: 0,
        minY: 0,
        width: 100,
        height: 100
      }
    },
    computed: {
      getViewBox: function() {
        return `${this.minX} ${this.minY} ${this.width} ${this.height}`;
      }
    }

  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    margin-top: 20px;
  }
  h3 {
    text-align: center;
    width: 250px;
    margin: 5px 0;
  }
  #app > div {
    width: 250px;
    margin-top: 5px;
  }
  span {
    font-size: 15px;
  }
  input {
    width: 250px;
    margin: 10px 0;
  }
  button {
    margin: 0 3px;
    border: 1px solid #a4a4a4;
    border-radius: 2px;
    background: white;
    outline: none;
    cursor: pointer;
    float: right;
  }
  .note {
    text-align: center;
    display: block;
    width: 250px;
    margin: 10px 0;
  }
  .svg {
    width: 250px;
    text-align: center;
  }
  svg {
    border: 1px solid gray;
  }
</style>
