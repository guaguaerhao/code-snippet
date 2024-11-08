### 1.上传图片/批量导入/创建本地 URL 显示/手动上传

``` js
<template>
    <el-upload
    style="margin-bottom:10px"
    ref="upload"
    :multiple="multiple"
    :limit="limit"
    :show-file-list="false"
    accept=".png, .jpg, .jpeg"
    :action="uploadFileUrl"
    :headers="headers"
    :file-list="fileList"
    :on-success="handleFileSuccess"
    :on-change="handleFileChange"
    :auto-upload="false" >
        <el-button>批量导入</el-button>
    </el-upload>
</template>
<script>
export default {
    data() {
        return {
            // 最多上传文件数
            limit: 100,
            // 是否支持批量上传
            multiple: true,
            // 上传中
            uploading: false,
            // 上传文件列表
            hasUploadedLength: 0,
            // 基础 URL
            baseUrl: process.env.VUE_APP_BASE_API,
            // 上传文件服务器地址
            uploadFileUrl: process.env.VUE_APP_BASE_API + "/common/upload",
            // 请求头
            headers: {
                Authorization: "Bearer " + getToken(),
            },
        }
    }
}
</script>
```