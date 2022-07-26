<template>
  <el-table :data="filterTableData" style="width: 40%" border>
    <el-table-column label="列名" prop="alias" />
    <el-table-column label="计算公式" prop="cal" />

    <el-table-column align="right">
      <template #default="scope">
        <el-button size="small" @click="handleEdit(scope.$index, scope.row)"
          >Edit</el-button
        >
        <el-button
          size="small"
          type="danger"
          @click="handleDelete(scope.$index, scope.row)"
          >Delete</el-button
        >
      </template>
    </el-table-column>
  </el-table>
</template>

<script lang="ts" setup>
import { computed, ref } from 'vue'

interface Column {
  alias: string
  cal: string
}

const search = ref('')
const filterTableData = computed(() =>
  tableData.filter(
    (data) =>
      !search.value ||
      data.alias.toLowerCase().includes(search.value.toLowerCase())
  )
)
const handleEdit = (index: number, row: Column) => {
  row.alias = 'hhh'
  console.log(index, row)
}
const handleDelete = (index: number, row: Column) => {
  console.log(index, row)
}

const tableData: Column[] = [
  {
    alias: '2016-05-03',
    cal: 'Tom',
  },
]
</script>