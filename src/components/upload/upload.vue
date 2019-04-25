<template>
  <div>
    <upload-Avatar 
      :tip="tip"
      :accept="accept"
      :action="action"
      :showFileList="showFileList"
      :avatarUrl="avatarUrl"
      :on-success="onSuccess"
    />
    <upload-List v-if="showFileList"
    :files="fileList" 
    :listType="listType"
    :on-remove="onRemove"/>
  </div>
</template>

<script>
  import uploadAvatar from './src/uploadAvatar'
  import UploadList from './src/uploadList'
  
  export default {
    components: {
      uploadAvatar,
      UploadList
    },
    props: {
      action: {
        type: String,
        required: true,
        default: 'baidu.com'
      },
      tip: {
        type: String,
        default: ''
      },
      accept: String,
      avatarUrl: String,
      onRemove: {
        type: Function,
        default: function () {}
      },
      onSuccess: {
        type: Function,
        default: function () {}
      },
      fileList: {
        type: Array,
        default () {
          return []
        }
      },
      listType: {
        type: String,
        default: 'text' // text,picture
      },
      showFileList: {
        type: Boolean,
        default: false
      },
      httpRequest: Function
    }
  }
</script>

<style lang="less" scoped>