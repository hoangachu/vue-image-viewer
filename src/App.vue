<template>
  <div id="app">
    <img width="25%" src="./assets/logo.png">
    <table>
      <thead>
        <tr>
          <th>Id</th>
          <th>Image</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(image, index) in allImages" :key="index">
          <td>{{ index }}</td>
          <td>
            <button type="button" @click="show(index)">Click to show</button>
          </td>
        </tr>
      </tbody>
    </table>
    <img-viewer ref="viewer"/>
  </div>
</template>

<script>
import ImgViewer from "./components/ImgViewer";

function genImages() {
  const sourceImages = [];
  const base = Math.floor(Math.random() * 60, 10) + 10;
  for (let i = 0; i < 10; i++) {
    sourceImages.push({
      thumbnail: `https://picsum.photos/id/${base + i}/300/200`,
      source: `https://picsum.photos/id/${base + i}/600/400`
    });
  }
  return sourceImages;
}

export default {
  name: "App",
  components: {
    ImgViewer
  },
  data() {
    return {
      allImages: [genImages(), genImages(), genImages()]
    };
  },
  methods: {
    show(index) {
      this.$refs.viewer.show(
        this.allImages[index],
        Math.floor(Math.random() * 10)
      );
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
