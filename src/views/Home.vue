<template>
  <div class="home">
    <Upload
      tip="只能上传jpg/png文件，且不超过500kb"
      accept="image/jpeg,image/jpg,image/png"
      :action="action"
      :showFileList="true"
      :fileList="fileList"
      :avatarUrl="avatarUrl"
      multiple
      :on-remove="handleRemove"
      :on-success="handleSuccess" 
    />
  </div>
</template>

<script>
// @ is an alias to /src
import upload from '@/components/upload/upload.vue'

export default {
  components: {
    upload
  },
  data () {
    return {
      action: '',
      avatarUrl: '',
      fileList: [
        {
          'alt': "医院大门",
          'name': "http://upload.samsph.com/2015/0818/20150818032909546.jpg"
        },
        {
          'alt': "门诊大厅",
          'name': "http://upload.samsph.com/2015/0818/20150818032905305.jpg"
        },
        {
          'alt': "第一住院大楼",
          'name': "http://upload.samsph.com/2015/0818/20150818032902730.jpg"
        }
      ]
    }
  },
  methods: {
    handleSuccess (response) {
      // console.log(response)
      this.avatarUrl = response.data.url
    },
    handleRemove (file, index) {
      // console.log(index)
      if (index || index === 0) {
        this.fileList.splice(index, 1)
      }
    }
  }
}
</script>
