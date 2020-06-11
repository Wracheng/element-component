<template>
  <el-pagination
    @current-change="handlePageChange"
    :page-size="10"
    layout="total,prev, pager, next"
    :total="total"
  ></el-pagination>
</template>

<script>
let dataGlobal = [];
export default {
  data() {
    return {
      total: 0,
      // data是所有的数据
      data: []
    };
  },
  created() {
    this.getData();
  },
  methods: {
    getData() {
      // 获取data真实数据获取到之后再执行下面三步
      dataGlobal = this.data;
      this.setPage(this.data.length);
      this.initPage();
    },
    // 配置分页基础数据
    setPage(total) {
      this.total = total;
    },
    initPage() {
      this.handlePageChange(1);
    },
    // 分页
    handlePageChange(currentPage) {
      this.data = dataGlobal.slice(10 * currentPage - 10, currentPage * 10);
    }
  }
};
</script>

<style>
</style>