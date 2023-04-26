Version
3.2.16

Environment
"vue": "3.2.40",

Reproduction link

Steps to reproduce

form表单校验，若表单元素有上传文件组件, 若点击此栏目表单的label，会触发上传事件，按理来说只有点击上传组件的上传按钮才会触发此上传事件。详见案例如下
<template>
  <a-form
    :model="formState"
    name="basic"
    :label-col="{ span: 8 }"
    :wrapper-col="{ span: 16 }"
  >
    <a-form-item label="上传文件" name="fileList" :rules="[{ required: true }]">
      <a-upload
        v-model:file-list="fileList"
        name="file"
        action="https://www.mocky.io/v2/5cc8019d300000980a055e76"
        :headers="headers"
        @change="handleChange"
      >
        <a-button>
          <upload-outlined></upload-outlined>
          Click to Upload
        </a-button>
      </a-upload>
    </a-form-item>
  </a-form>
</template>
<script>
import { defineComponent, reactive } from "vue";
export default defineComponent({
  setup() {
    const formState = reactive({
      fileList: [],
    });

    return {
      formState,
    };
  },
});
</script>

What is expected?
点击此栏目的label，不会触发上传事件

What is actually happening?
点击此栏目的label，会触发事件
