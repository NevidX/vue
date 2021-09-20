
<template>
  <div class="wrapper">
    <div :style="{ 'margin-left': `${depth * 20}px` }" class="folder">
      <span><img src="../img/icons/folder1.svg" alt="folder" /></span>{{ name }}
    </div>
    <template v-for="folder in folders">
      <!-- eslint-disable-next-line -->
      <FolderView
        :name="folder.name"
        :folders="folder.folders"
        :files="folder.files"
      />
    </template>
    <template v-for="file in files">
      <!-- eslint-disable-next-line -->
      <FileView :name="file.name" />
    </template>
  </div>
</template>

<script>
import FileView from "./FileView";
export default {
  name: "FolderView",
  components: { FileView },
  props: {
    name: String,
    folders: Array,
    files: Array,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.wrapper {
  width: 400px;
  height: auto;
  margin: 0 auto;
  .folder {
    font-weight: bold;
    position: relative;
    color: red;
    font-size: 20px;
    margin-bottom: 60px;
    span {
      display: block;
      position: absolute;
      top: -15px;
      left: -50px;
      transform: scale(0.5);
    }
  }
}
</style>
