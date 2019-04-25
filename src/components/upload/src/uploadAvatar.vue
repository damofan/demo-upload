<template>
  <div class="fox-upload">
    <div class="uploader">
      <div class="avatar-uploader">
        <div class="fox-upload-icon">
          <img v-if="avatarUrl" :src="avatarUrl" alt="avatar" class="avatar">
          <div v-else>
            <i class="iconfont">&#xe6f3;</i>
            <p class="text">添加图片</p>
          </div>
        </div>
      </div>
      <input class="fox-upload-input" type="file" name="file" multiple="multiple"
        @change="handleChange"
        :accept="accept"
      />
    </div>
    <div v-if="tip" class="fox-upload-tip">{{tip}}</div>
  </div>
</template>

<script>
  import { setTimeout } from 'timers'
  export default {
    props: {
      accept: String,
      tip: String,
      avatarUrl: String,
      onSuccess: Function,
      showFileList: Boolean
    },
    methods: {
      handleChange (ev) {
        const files = ev.target.files
        if (!files) return
        this.uploadFiles(files)
      },
      uploadFiles () {
        // 模拟上传后返回文件相关数据
        setTimeout(()=>{
          // console.log('上传成功啦～')
        },1000)
      }
    }
  }
</script>

<style lang="less" scoped>
  .fox-upload-input{
    display: block;
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    opacity: 0;
  }
  .uploader{
    position: relative;
    display: inline-block;
  }
  .avatar-uploader{
    display: table;
    width: 104px;
    height: 104px;
    position: relative;
    font-size: 14px;
    text-align: center;
    vertical-align: top;
    background-color: #fafafa;
    border: 1px dashed #d9d9d9;
    border-radius: 4px;
    cursor: pointer;
    .fox-upload-icon{
      display: table-cell;
      width: 100%;
      height: 100%;
      padding: 8px;
      text-align: center;
      vertical-align: middle;
      .avatar{
        display: block;
        width: 100%;
        height: 100%;
      }
      .iconfont{
        font-size: 32px;
        color: #999;
      }
      .text{
        margin-top: 8px;
        color: #666;
      }
    }
  }
  .button-uploader{
    padding-bottom: 8px;
    button{
      background-color: #4caf50;
      display: inline-block;
      padding: 0 1.32em;
      line-height: 2.3;
      font-size: 13px;
      border-width: 0;
      outline: 0;
      -webkit-appearance: none;
      position: relative;
      margin-left: auto;
      margin-right: auto;
      padding-left: 14px;
      padding-right: 14px;
      box-sizing: border-box;
      text-align: center;
      text-decoration: none;
      color: #fff;
      border-radius: 5px;
      -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
      overflow: hidden;
    }
  }
  .fox-upload-tip{
    font-size: 12px;
    opacity: .6;
    margin-bottom: 10px;
  }
</style>