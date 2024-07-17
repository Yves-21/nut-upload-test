<!--
 * @Author: liyiwei
 * @Date: 2024-07-17 18:20:45
 * @LastEditors: liyiwei
 * @LastEditTime: 2024-07-17 18:57:48
 * @FilePath: /nut-upload-test/src/pages/index/index.vue
 * @Description: 
 * 
 * Copyright (c) 2024 by 零碳产业运营中心, All Rights Reserved. 
-->
<template>
  <view class="demo">
    <view>
      欢迎使用 NutUI 开发 Taro 多端项目
      <Dongdong />
    </view>
    <view>
      <nut-uploader :url="uploadUrl" :source-type="['album', 'camera']" accept="image/*" v-model:file-list="fileList"
        maximum="6" multiple @success="uploadSuccess" @delete="onDeleteFile">
      </nut-uploader>
    </view>
  </view>
</template>

<script setup>
import { reactive, ref } from 'vue';
import { Dongdong } from '@nutui/icons-vue-taro';

const uploadUrl = reactive('https://xxxx');
const fileList = reactive([]);

const uploadSuccess = (fileResult) => {
  const { responseText, option, fileItem } = fileResult
  let res = responseText.data
  res = JSON.parse(res)
  console.log('上传成功：', res, fileList)
};
const onDeleteFile = (fileResult) => {
  const { files, fileList, index } = fileResult
  console.log('删除文件', fileList)
}
</script>

<style>
.demo {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>