<template>
  <div class="file-template">
    <div class="file-template__folder-section folder-section">
      <div class="folder-section__logo">
        <span class="explorer-logo"
          ><img src="./img/icons/explorer.svg" alt=""
        /></span>
        File Explorer
      </div>
      <div class="folder-section__content">
        <FolderView name="Files" :folders="folders" :files="files" />
      </div>
    </div>
    <div class="file-template__working-section working-section">
      <div class="working-section__tools-panel tools-panel">
        <div class="tools-panel__buttons">
          <div class="btn btn__left">&larr;</div>
          <div class="btn btn__right">&rarr;</div>
          <div class="btn btn__search">
            <img src="./img/icons/search1.svg" alt="search" />
          </div>
          <div class="btn btn__document">
            <img src="./img/icons/document.svg" alt="document" />
          </div>
          <div class="btn btn__share">
            <img src="./img/icons/share.svg" alt="share" />
          </div>
          <div class="btn btn__watch">
            <img src="./img/icons/binoculars.svg" alt="watch" />
          </div>
        </div>
        <div class="tools-panel__app-buttons">
          <div class="btn btn__hide-window">&minus;</div>
          <div class="btn btn__resize">&harr;</div>
          <div class="btn btn__close">&times;</div>
        </div>
      </div>
      <div class="working-section__file-view">
        <FolderView name="Files" :folders="folders" :files="files" />
      </div>
    </div>
  </div>
</template>

<script>
import FolderView from "./components/FolderView.vue";
import FileView from "./components/FileView.vue";
import FileTemplate from "./components/FileTemplate.vue";
import data from "./data/list";

export default {
  name: "App",
  components: {
    FolderView,
    FileView,
    FileTemplate,
  },
  data: () => data,
};
</script>

<style lang="scss">
#app {
  width: 100%;
  font-family: "Lato", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-image: url(img/background.jpg);
  padding: 30px 0 30px 0;
  height: 100vh;
  @media (max-width: 1000px) {
    padding: 0;
  }
  .file-template {
    display: flex;
    margin: 0 auto;
    width: 90%;
    height: 100%;
    border-radius: 5px;
    background-color: rgba(235, 235, 235, 0.63);
    backdrop-filter: blur(5px);
    @media (max-width: 1000px) {
      width: 100%;
    }
  }
  // FOLDER SECTION
  .file-template__folder-section {
    max-width: 400px;
    height: 100%;
    background-color: rgba(202, 202, 202, 0.425);
    overflow: hidden;
    border-radius: 5px;
  }
  .folder-section__content {
    height: 100%;
    overflow-y: auto;
    overflow-x: hidden;
  }
  .folder-section__logo {
    display: flex;
    margin-left: 10px;
    margin-bottom: 50px;
    max-width: 200px;
    align-items: center;
    font-size: 20px;
    border-bottom: 2px solid black;
  }
  .explorer-logo {
  }
  // WORKING SECTION
  .file-template__working-section {
    width: 100%;
    border-radius: 5px;
  }
  // TOOLS PANEL
  .working-section__tools-panel {
    width: 100%;
    height: 50px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-left: 10px;
  }
  .tools-panel__buttons {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 400px;
    transition: all 0.3s ease-in-out;
  }
  .btn {
    cursor: pointer;
    transition: all 0.3s linear;
    font-size: 40px;
    &:hover {
      transform: scale(1.05);
    }
  }
  .btn__left,
  .btn__right {
    &:hover {
      transform: scale(1);
    }
  }
  .tools-panel__app-buttons {
    display: flex;
    justify-content: space-between;
    width: 150px;
    margin-right: 40px;
  }
  .btn__resize {
    font-size: 30px;
    transform: rotate(130deg);
    &:hover {
      transform: rotate(130deg) scale(1.05);
    }
  }
  .tools-panel__search {
    font-size: 20px;
    margin-left: 10px;
    cursor: pointer;
  }
}
</style>
