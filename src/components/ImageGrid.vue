<template>
  <div class="gallery">
    <div class="controls">
      <button @click="filterSelection = 'All'">All</button>
      <button v-for="opt in filterOptions" :key="opt.index">{{ opt }}</button>
    </div>
    <div class="container">
      <gallery :images="imageURLS" :index="index" @close="index = null"></gallery>
      <img
        class="image"
        v-for="(image, imageIndex) in imageFilter"
        :key="imageIndex"
        @click="index = imageIndex"
        :src="urlBase + image.Key"
        :data="image.Content"
      />
    </div>
  </div>
</template>

<script>
import AWS from "aws-sdk";
import VueGallery from "vue-gallery";

const s3 = new AWS.S3();

export default {
  loading: false,
  name: "ImageGrid",
  props: {},

  data() {
    return {
      errors: "",
      selected: "",
      loading: false,
      images: [],
      imageURLS: [],
      filterOptions: [],
      filterSelection: "All",
      filteredImages: [],
      // @TODO url ENV
      urlBase: "",
      index: null
    };
  },

  methods: {
    async loadImages() {
      this.loading = true;
      // @TODO access ENV
      s3.config.update({
        accessKeyId: "",
        secretAccessKey: "",
        region: "ap-southeast-2"
      });
      // @TODO Bucket ENV
      const params = { Bucket: "" };
      const response = await s3
        .listObjects(params, err => {
          if (err) {
            console.log(err);
          }
        })
        .promise();
      this.loading = false;

      const keys = {};
      for (var key in response.Contents) {
        this.images.push(response.Contents[key]);
        this.imageURLS.push(this.urlBase + response.Contents[key].Key);
        let x = response.Contents[key].Key.split("-")[0].replace("_", " ");
        //e.g New_Zealand
        keys[x] = x;
      }
      this.filterOptions = Object.keys(keys);
      this.images = response.Contents;
      return this.images;
    }
  },

  computed: {
    imageFilter() {
      return this.filterSelection !== "All"
        ? this.images.filter(
            image => image.Key.split("-")[0] === this.filterSelection
          )
        : this.images;
    }
  },

  async created() {
    this.loadImages();
  },
  components: {
    gallery: VueGallery
  }
};
</script>

<style scoped lang="scss">
.container {
  max-width: 100vw;
  color: white;
  display: inline-block;
  width: 100%;
  text-align: center;
  font-family: system-ui;
  font-weight: 900;
  font-size: 2rem;
  overflow: hidden;
  -moz-column-count: 2;
  -moz-column-gap: 10px;
  -webkit-column-count: 2;
  -webkit-column-gap: 10px;
  column-count: 3;
  column-gap: 10px;
  width: 90%;
  transition: all 1.5s ease-in-out;
}
.controls {
  width: 100%;
  display: flex;
  justify-content: space-around;
  margin-bottom: 40px;
  button {
    display: flex;
  }
}
.image {
  display: inline-block;
  margin-bottom: 0px;
  width: auto;
  max-width: 100%;
  object-fit: cover;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  transition: all 1.5s ease;
}
.container:hover > .image {
  filter: grayscale(100%);
  filter: brightness(0.7);
}
.container:hover > .image:hover {
  filter: grayscale(0%);
  filter: brightness(1);
}
</style>
