<template>
  <div>
    <transition-group tag="ul" v-if="files.length"
      :class="[
        'upload-list',
        'upload-list-' + listType
      ]"
    >
      <li v-for="(file, index) in files" :key="file.url" class="upload-list_item">
        <div class="upload-list_item_info">
          <img :src="file.name" :alt="file.name" class="info-img">
          <input type="hidden" name="url" v-model="file.url">
          <span class="upload-list_item_name"><input type="text" name="title" v-model="file.name" class="alt"></span>
        </div>
        <span class="iconfont upload-list_item_delete" @click="onRemove(files, file, index)">&#xe640;</span>
      </li>
    </transition-group>
  </div>
</template>

<script>
  export default {
    props: {
      files: {
        type: Array,
        default () {
          return []
        }
      },
      listType: String,
      onRemove: Function
    }
  }
</script>

<style lang="less" scoped>
  .upload-list{
    border-top: 1px solid #d9d9d9;
    border-bottom: 1px solid #d9d9d9;
    padding-top: 8px;
    padding-bottom: 8px;
    &.upload-list-picture{
      .upload-list_item{
        height: 34px;
        .upload-list_item_info{
          .upload-list_item_name{
            padding-left: 54px;
          }
        }
      }
    }
    &.upload-list-text{
      .upload-list_item{
        height: 34px;
        .upload-list_item_info{
          .upload-list_item_name{
            padding-left: 0;
            input.alt {
              padding-left: 28px;
            }
          }
        }
      }
    }
    .upload-list_item{
      margin-top: 8px;
      font-size: 14px;
      height: 34px;
      position: relative;
      padding-left: 15px;
      padding-right: 15px;
      .upload-list_item_info{
        position: relative;
        .info-img, .info-text {
          position: absolute;
          top: 0;
          left: 0;
          line-height: 34px;
        }
        .info-img{
          width: 44px;
          height: 34px;
        }
        .info-text{
          width: 30px;
          height: 34px;
          text-align: center;
          opacity: .5;
        }
        .upload-list_item_name{
          display: block;
          padding-right: 34px;
          input.alt{
            display: block;
            height: 34px;
            border: 1px solid #d9d9d9;
            width: 100%;
            background-color: transparent;
            border-radius: 4px;
            padding: 0 5px;
          }
        }
      }
      .upload-list_item_delete{
        position: absolute;
        top: 3px;
        right: 15px;
        height: 28px;
        width: 28px;
        line-height: 1;
        opacity: 1;
        border: 1px solid #ea6f5a;
        border-radius: 4px;
        text-align: center;
        line-height: 28px;
        color: #fff;
        background-color: #ea6f5a
      }
    }
  }
</style>