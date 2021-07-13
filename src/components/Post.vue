<template>
  <div>
    <el-card class="box-card mt-2 mb-2">
      <div slot="header" class="clearfix">
        <span>id: {{ id }}</span>
        <el-button style="float: right; padding: 3px 0" type="text"
          >Operation button</el-button
        >
      </div>
      <div v-html="text"></div>
    </el-card>
  </div>
</template>

<script>
export default {
  props: {
    id: Number,
    text: String,
  },
};
</script>

<style scoped>
.text {
  font-size: 14px;
}

.item {
  margin-bottom: 18px;
}

.clearfix:before,
.clearfix:after {
  display: table;
  content: "";
}
.clearfix:after {
  clear: both;
}

.box-card {
  width: 100hh;
}
</style>