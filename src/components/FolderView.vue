
<template>
  <div class="wrapper">
    <div class="folder__wrapper">
      <div
        @click="opened = !opened"
        :style="{ 'margin-left': `${depth * 20}px` }"
        class="folder"
      >
        <span v-if="opened" class="folder-icon"
          ><img src="../img/icons/folder.svg" alt="folder"
        /></span>
        <span v-else class="closed-folder-icon">
          <img src="../img/icons/ClosedFolder.svg" alt="folder" />
        </span>
        {{ name }}
      </div>
    </div>
    <template v-for="folder in folders">
      <!-- eslint-disable-next-line -->
      <FolderView
        v-if="opened"
        :name="folder.name"
        :folders="folder.folders"
        :files="folder.files"
        :depth="depth + 1"
      />
    </template>
    <template v-for="file in files">
      <!-- eslint-disable-next-line -->
      <FileView
        v-if="opened"
        :name="file.name"
        :file="file.files"
        :depth="depth + 1"
      />
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
    depth: {
      type: Number,
      default: 0,
    },
  },
  data() {
    return {
      opened: false,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.wrapper {
  width: 350px;
  max-height: 100%;

  .folder__wrapper {
    width: 100%;
    height: 100%;
  }
  .folder {
    display: flex;
    width: 100%;
    font-weight: bold;
    position: relative;
    color: rgb(73, 73, 73);
    text-align: left;
    align-items: center;
    font-size: 20px;
    padding-left: 10px;
    margin-bottom: 10px;
    cursor: pointer;
    transition: all 0.2s ease-in-out;
    border-bottom: 1px solid gray;
    border-radius: 100px;
    user-select: none;
    &:hover {
      background-color: rgba(17, 118, 233, 0.336);
      border-left: 3px solid rgba(17, 118, 233, 0.336);
    }
    .folder-icon,
    .closed-folder-icon {
      margin-right: 5px;
      display: block;
    }
  }
}
</style>
