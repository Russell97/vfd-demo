<template>
  <div class="hello">
    <div class="vfd-container">
      <vfd ref="vfd" :style="vfdHeight" />
    </div>
    <!-- <vfd /> -->
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
    // // 时间轴数据
    // let tData = JSON.parse(this.timeLineData);
    // // 添加节点
    // tData.map((item, index) => {
    //   this.showData.nodeList.push({
    //     type: "child-flow",
    //     nodeName: item.statusType,
    //     icon: "ChildFlowIcon",
    //     id: String(item.id),
    //     height: 50,
    //     x: 100,
    //     width: 50,
    //     y: 200 + index * 100,
    //     status: item.status,
    //     background: '#67C23A'
    //   });
    // });
    // // 添加节点连接线
    // this.showData.nodeList.map((item, index) => {
    //   if (this.showData.nodeList[index + 1]) {
    //     this.showData.linkList.push({
    //       type: "link",
    //       sourceId: String(this.showData.nodeList[index].id),
    //       targetId: String(this.showData.nodeList[index + 1].id),
    //       cls: {
    //         linkType: "Flowchart",
    //         linkColor: "#2a2929"
    //       }
    //     });
    //   }
    // });

    // this.vfdHeight =  `height: ${(this.showData.nodeList.length + 2) * 100 + 200}px`

    // // 新增 开始节点
    // this.showData.nodeList.unshift({
    //   type: "start",
    //   nodeName: "开始",
    //   icon: "StartIcon",
    //   id: "start",
    //   height: 50,
    //   x: 135,
    //   width: 50,
    //   y: 100
    // });
    // let startLine = JSON.parse(JSON.stringify(this.showData.linkList[0]))
    // startLine.targetId = startLine.sourceId
    // startLine.sourceId = 'start'
    // this.showData.linkList.unshift(startLine)

    // // 新增 结束节点
    // this.showData.nodeList.push({
    //   type: "end",
    //   nodeName: "结束",
    //   icon: "EndIcon",
    //   id: "end",
    //   height: 50,
    //   x: 135,
    //   width: 50,
    //   y: 100 + this.showData.nodeList.length * 100
    // });
    // let endLine = JSON.parse(JSON.stringify(this.showData.linkList[this.showData.linkList.length-1]))
    // endLine.sourceId = endLine.targetId
    // endLine.targetId = 'end'
    // this.showData.linkList.push(endLine)

    // // 新增 节点分支
    // let dataArr = [];
    // this.showData.nodeList.map((item, index) => {
    //   if (item.status === 2) {
    //     let data = JSON.parse(JSON.stringify(item));
    //     data.id = `-${item.id}`;
    //     data.nodeName = "审核不成功";
    //     data.x = 250;
    //     data.background = ''
    //     dataArr.push(data);
    //   }
    // });
    // this.showData.nodeList = [...this.showData.nodeList, ...dataArr];

    // console.log(this.showData);
    // this.$refs.vfd.loadFlow(JSON.stringify(this.showData));

    this.stateContainer.stateData.map((item, index) => {
      this.showData.nodeList.push({
        type: "child-flow",
        nodeName: item.statusTitle,
        icon: "ChildFlowIcon",
        id: String(item.id),
        height: 50,
        x: 100,
        width: 50,
        y: 200 + index * 100,
        status: item.statusId,
        background: '#67C23A'
      });
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
          showGrid: true,
          showGridText: "显示网格",
          showGridIcon: "eye"
        },
        status: "1",
        remarks: []
      },
      timeLineData:
        '[{"id":45,"name":"大叶凤尾","reviewer_name":"admin","status":2,"remark":"","create_time":"2020-08-20 13:38:17","statusType":"审核成功"},{"id":44,"name":"大叶凤尾","reviewer_name":"admin","status":2,"remark":"","create_time":"2020-08-20 13:38:09","statusType":"审核成功"},{"id":43,"name":"大叶凤尾","reviewer_name":"admin","status":1,"remark":"","create_time":"2020-08-20 13:38:00","statusType":"提交审核"},{"id":42,"name":"大叶凤尾","reviewer_name":"admin","status":4,"remark":"1","create_time":"2020-08-20 13:37:49","statusType":"已驳回"}]',
      vfdHeight: 'height: 1000px;',
      stateContainer: {
        doubleCheck: [],
        stateData: [
          {
            statusId: 1,
            statusTitle: '未审核'
          },
          {
            statusId: 2,
            statusTitle: '已审核'
          },
          {
            statusId: 3,
            statusTitle: '已复核'
          },
          {
            stateId: 4,
            statusTitle: '已审核'
          },
          {
            statusId: 5,
            statusTitle: '已驳回'
          }
        ]
      }
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
      // height: 1500px;
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
