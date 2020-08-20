<template>
  <div class="hello">
    <div class="vfd-container">
      <vfd ref="vfd" :canvasHeight="canvasHeight" />
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
    this.$refs.vfd.loadFlow(this.showData)
  },
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
      showData:
        '{"nodeList":[{"type":"child-flow","nodeName":"网关","icon":"ChildFlowIcon","id":"1","height":50,"x":100,"width":50,"y":100},{"type":"child-flow","nodeName":"人工节点","icon":"ChildFlowIcon","id":"2","height":50,"x":100,"width":120,"y":200},{"type":"child-flow","nodeName":"人工节点","icon":"ChildFlowIcon","id":"3","height":50,"x":100,"width":120,"y":300}],"linkList":[{"type":"link","sourceId":"1","targetId":"2","cls":{"linkType":"Flowchart","linkColor":"#2a2929"}},{"type":"link","sourceId":"2","targetId":"3","cls":{"linkType":"Flowchart","linkColor":"#2a2929"}}],"attr":{"id":""},"config":{"showGrid":false,"showGridText":"显示网格","showGridIcon":"eye"},"status":"1","remarks":[]}',
      canvasHeight: 'height: 1500px'
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
      width: 500px;
      height: 1500px;
    }
  }
}
</style>
