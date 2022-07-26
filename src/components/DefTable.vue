<template>
 <el-form
    border
    ref="ruleFormRef"
    :model="ruleForm"
    :rules="rules"
    label-width="120px"
    class="demo-ruleForm"
    status-icon
    width="1000px"
  >
  <p style="text-align:left;">数据源</p>
    <el-form-item label="唯一标识" prop="name">
      <el-input v-model="ruleForm.name" placeholder="t01"/>
    </el-form-item>
    <el-form-item label="库名" prop="databaseName">
      <el-input v-model="ruleForm.databaseName" placeholder="default"/>
    </el-form-item>
    <el-form-item label="表名" prop="tableName">
      <el-input v-model="ruleForm.tableName" placeholder="ods_xxx"/>
    </el-form-item>
    <el-form-item label="筛选条件" prop="where">
      <el-input v-model="ruleForm.where" type="textarea" />
    </el-form-item>

    <def-column width="1000px"/>

  </el-form>
</template>


<script lang="ts" setup>
import { reactive, ref } from 'vue'
import type { FormInstance, FormRules } from 'element-plus'

const formSize = ref('default')
const ruleFormRef = ref<FormInstance>()
const ruleForm = reactive({
  name: '',
  databaseName: '',
  tableName: '',
  where: '',
})

const rules = reactive<FormRules>({
  name: [
    { required: true, message: '请输入唯一标识', trigger: 'blur' },
  ],
  databaseName: [
    { required: true, message: '请输入库名', trigger: 'blur' },
  ],
  tableName: [
    { required: true, message: '请输入表名', trigger: 'blur' },
  ],
  where: [
    { required: true, message: '请输入筛选条件', trigger: 'blur' },
  ],
})

const submitForm = async (formEl: FormInstance | undefined) => {
  if (!formEl) return
  await formEl.validate((valid, fields) => {
    if (valid) {
      console.log('submit!')
    } else {
      console.log('error submit!', fields)
    }
  })
}

const resetForm = (formEl: FormInstance | undefined) => {
  if (!formEl) return
  formEl.resetFields()
}

const options = Array.from({ length: 10000 }).map((_, idx) => ({
  value: `${idx + 1}`,
  label: `${idx + 1}`,
}))
</script>