<template>
  <div id="app" @click="incrementCounter" class="clickable-area">
    <h1>Eva Latifah Project</h1>

    <!-- Click Counter -->
    <div class="counter-section">
      <p>Count: {{ counter }}</p>
      <button @click.stop="undoClick">Undo Click</button>
    </div>

    <!-- Box Color Changer -->
    <div class="color-changer-section">
      <div :style="{ backgroundColor: boxColor }" class="color-box"></div>
      <div class="color-changer-controls">
        <button @click="changeColor">Change Color</button>
      </div>
    </div>

    <!-- Image Carousel -->
    <div class="carousel-section">
      <img :src="images[currentImage]" class="carousel-image" />
      <div class="carousel-controls">
        <button @click="prevImage">Previous</button>
        <button @click="nextImage">Next</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // For Click Counter
      counter: 0,
      lastCounterValue: 0,

      // For Box Color Changer
      boxColor: '#FFB6C1',  // Default pastel color
      colors: [
        '#FFB6C1',  // Light Pink
        '#FFCCCB',  // Light Red
        '#D3F8E2',  // Light Green
        '#BFD3C1',  // Light Olive
        '#B4E1FF',  // Light Blue
        '#D1C4E9',  // Light Purple
        '#F7E5E5',  // Light Peach
        '#E2B4D1',  // Light Rose
        '#F3E1E1',  // Light Coral
        '#E3F2FD'   // Light Sky Blue
      ],

      // For Image Carousel
      images: [
        'https://i.pinimg.com/736x/ae/da/12/aeda12b86b22ae42893599abdfa76a99.jpg', 
        'https://i.pinimg.com/736x/4a/c6/40/4ac64058991f8cd5edfce3b5e9a9365f.jpg',
        'https://i.pinimg.com/736x/4b/bd/8e/4bbd8e58e4e7a3973324d2441527bd45.jpg',
        'https://i.pinimg.com/736x/bd/d3/e9/bdd3e955d2455f0f4263686bcc1811cc.jpg',
        'https://i.pinimg.com/736x/6a/3e/e5/6a3ee56550103611ae6d18e46c4779ef.jpg'
      ],
      currentImage: 0
    };
  },
  methods: {
    // Method for click counter
    incrementCounter() {
      this.lastCounterValue = this.counter;
      this.counter++;
    },

    // Method for undoing the click
    undoClick() {
      this.counter = this.lastCounterValue;
    },

    // Method for color changer
    changeColor() {
      const randomIndex = Math.floor(Math.random() * this.colors.length);
      this.boxColor = this.colors[randomIndex];
    },

    // Methods for image carousel
    prevImage() {
      if (this.currentImage > 0) {
        this.currentImage--;
      } else {
        this.currentImage = this.images.length - 1;
      }
    },
    nextImage() {
      if (this.currentImage < this.images.length - 1) {
        this.currentImage++;
      } else {
        this.currentImage = 0;
      }
    }
  }
};
</script>

<style>
#app {
  text-align: center;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  position: relative;
}

.clickable-area {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.counter-section {
  margin-bottom: 20px;
}

.color-changer-section {
  width: 100vw;
  height: 100vh;
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.color-box {
  width: 100vw;
  height: 100vh;
  background-color: #FFB6C1;  /* Default pastel color */
  position: absolute;
  top: 0;
  left: 0;
  z-index: -1;
  box-shadow: 0 0 30px rgba(255, 255, 255, 0.6); /* Glow effect */
}

.color-changer-controls {
  position: absolute;
  right: 20px;
  bottom: 20px;
  
}

.carousel-section {
  margin-top: 20px;
}

.carousel-image {
  width: 300px;
  height: 300px;
  margin: 20px 0;
  border: 5px solid #333; 
  border-radius: 10px; 

}

.carousel-controls button {
  margin: 0 10px;
}
</style>
