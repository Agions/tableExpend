<template>
  <el-table :data="data" stripe style="width: 100%">
    <template v-for="(column, index) in columns">
      <el-table-column
        :prop="column.prop"
        :key="index"
        :label="column.label"
        :width="column.width"
      >
        <template slot-scope="{ row, $index }">
          <TableExtend
            v-if="column.render"
            :render="column.render"
            :row="row"
            :index="$index"
            :column="column"
          ></TableExtend>
          <template v-else>{{ row[column.prop] }}</template>
        </template>
      </el-table-column>
    </template>
  </el-table>
</template>
<script>
import TableExtend from "./TableExtend";
export default {
  name: "TabelBase",
  props: {
    data: { type: Array, default: () => [] },
    columns: { ype: Array, default: () => [] }
  },
  components: {
    TableExtend
  }
};
</script>
