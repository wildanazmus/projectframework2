<template>
  <div id="app" class="app-container">
    <h1>Vue.js App</h1>

    <!-- Click Counter -->
    <h3>Click Counter</h3>
    <p>Button clicked: {{ counter }} times</p>
    <button @click="incrementCounter">Click me</button>

    <!-- Box Color Changer -->
    <h3>Box Color Changer</h3>
    <div :style="{ backgroundColor: boxColor }" class="box"></div>
    <button @click="changeColor">Change Color</button>

    <!-- Image Carousel -->
    <h3>Image Carousel</h3>
    <div class="carousel-container">
      <button @click="prevImage">Previous</button>
      <div class="carousel">
        <img :src="images[currentImage]" alt="carousel image" />
      </div>
      <button @click="nextImage">Next</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // Click Counter
      counter: 0,

      // Box Color Changer
      colors: ["#ff0000", "#00ff00", "#0000ff", "#ff9900", "#9900ff"],
      currentColorIndex: 0,

      // Image Carousel
      images: ["https://via.placeholder.com/350x150/ff7f7f", "https://via.placeholder.com/350x150/7f7fff", "https://via.placeholder.com/350x150/7fff7f"],
      currentImage: 0,
    };
  },
  methods: {
    // Click Counter
    incrementCounter() {
      this.counter++;
    },

    // Box Color Changer
    changeColor() {
      this.currentColorIndex = (this.currentColorIndex + 1) % this.colors.length;
    },

    // Image Carousel
    prevImage() {
      this.currentImage = (this.currentImage - 1 + this.images.length) % this.images.length;
    },
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.images.length;
    },
  },
  computed: {
    boxColor() {
      return this.colors[this.currentColorIndex];
    },
  },
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
}

.app-container {
  background-color: white;
  border-radius: 15px;
  padding: 30px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
  width: 400px;
  margin: 50px auto;
  text-align: center;
}

h1 {
  color: #333;
}

button {
  background-color: #6200ea;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  margin: 10px;
}

button:hover {
  background-color: #3700b3;
}

.box {
  width: 100px;
  height: 100px;
  margin: 20px auto;
}

.carousel img {
  width: 100%;
  border-radius: 10px;
}

.carousel-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px 0;
}
</style>
