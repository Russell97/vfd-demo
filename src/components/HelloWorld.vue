<template>
  <div class="hello">
    <div class="vfd-container">
      <vfd ref="vfd" />
    </div>
  </div>
</template>

<script>
import vfd from "vfd";

export default {
  name: "HelloWorld",
  components: {
    vfd
  },
  mounted() {
    let tData = JSON.parse(this.timeLineData);
    tData.map((item, index) => {
      this.showData.nodeList.push({
        type: "child-flow",
        nodeName: item.statusType,
        icon: "ChildFlowIcon",
        id: String(item.id),
        height: 50,
        x: 100,
        width: 50,
        y: 100 + index * 100
      });
      if (tData[index + 1]) {
        this.showData.linkList.push({
          type: "link",
          sourceId: String(tData[index].id),
          targetId: String(tData[index+1].id),
          cls: {
            linkType: "Flowchart",
            linkColor: "#2a2929"
          }
        });
      }
    });
    this.$refs.vfd.loadFlow(JSON.stringify(this.showData));
  },
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
      showData: {
        nodeList: [],
        linkList: [],
        attr: {
          id: ""
        },
        config: {
          showGrid: false,
          showGridText: "显示网格",
          showGridIcon: "eye"
        },
        status: "1",
        remarks: []
      },
      timeLineData:
        '[{"id":45,"name":"大叶凤尾","reviewer_name":"admin","status":2,"remark":"","create_time":"2020-08-20 13:38:17","statusType":"审核成功"},{"id":44,"name":"大叶凤尾","reviewer_name":"admin","status":2,"remark":"","create_time":"2020-08-20 13:38:09","statusType":"审核成功"},{"id":43,"name":"大叶凤尾","reviewer_name":"admin","status":1,"remark":"","create_time":"2020-08-20 13:38:00","statusType":"提交审核"},{"id":42,"name":"大叶凤尾","reviewer_name":"admin","status":4,"remark":"1","create_time":"2020-08-20 13:37:49","statusType":"已驳回"}]'
    };
  }
};
</script>

<style lang="scss" scoped>
.hello {
  position: relative;
  top: 0;
  left: 0;
  .vfd-container {
    position: absolute;
    top: 0;
    right: 0;
    width: 500px;
    height: 500px;
    overflow: auto;
    /deep/ .ant-layout-sider {
      display: none;
    }
    /deep/ .ant-layout {
      width: 100%;
      height: 1500px;
      // .ant-layout-header {
      //   display: none;
      // }
      // .ant-layout-footer {
      //   display: none;
      // }
    }
  }
}
</style>
