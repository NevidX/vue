<template>
  <FolderView name="Folders" :folders="folders" :files="files" />
</template>

<script>
import FolderView from "./components/FolderView.vue";
import FileView from "./components/FileView.vue";
import data from "./data/list";

export default {
  name: "App",
  components: {
    FolderView,
    FileView,
  },
  data: () => data,
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
