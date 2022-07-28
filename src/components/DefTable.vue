<template>
 <el-form
    border
    ref="defTableRef"
    :model="defTable"
    :rules="rules"
    label-width="120px"
    class="demo-ruleForm"
    status-icon
    style="width: 40%"
  >
    <p style="text-align:left;">数据源</p>
    <el-form-item label="唯一标识" prop="name">
      <el-input v-model="defTable.name" placeholder="t01"/>
    </el-form-item>
    <el-form-item label="库名" prop="databaseName">
      <el-input v-model="defTable.databaseName" placeholder="default"/>
    </el-form-item>
    <el-form-item label="表名" prop="tableName">
      <el-input v-model="defTable.tableName" placeholder="ods_xxx"/>
    </el-form-item>
    <el-form-item label="筛选条件" prop="where">
      <el-input v-model="defTable.where" type="textarea" />
    </el-form-item>

    <p style="text-align:left;">每列的计算公式</p>

    <def-column/>

    <br>
    <el-form-item>
      <el-button type="primary" @click="submitForm(defTableRef)">看下</el-button>
    </el-form-item>

  </el-form>
</template>


<script lang="ts" setup>
import { reactive, ref } from 'vue'
import type { FormInstance, FormRules } from 'element-plus'

const defTableRef = ref<FormInstance>()
const defTable = reactive({
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
    alert(JSON.stringify(formEl))
}

</script>