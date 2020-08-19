<template>
  <div class="hello">
    <vfd :showData="showData" />
  </div>
</template>

<script>
import vfd from "vfd";

export default {
  name: "HelloWorld",
  components: {
    vfd
  },
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
      showData:
        '{"nodeList":[{"type":"child-flow","nodeName":"网关","icon":"ChildFlowIcon","id":"1","height":50,"x":3610,"width":50,"y":3080,"tx":3610,"ty":3230},{"type":"child-flow","nodeName":"人工节点","icon":"ChildFlowIcon","id":"2","height":50,"x":3610,"width":120,"y":3230,"tx":3610,"ty":3230},{"type":"child-flow","nodeName":"人工节点","icon":"ChildFlowIcon","id":"3","height":50,"x":3610,"width":120,"y":3380,"tx":3610,"ty":3380}],"linkList":[{"type":"link","sourceId":"1","targetId":"2","cls":{"linkType":"Flowchart","linkColor":"#2a2929","linkThickness":2}},{"type":"link","sourceId":"2","targetId":"3","cls":{"linkType":"Flowchart","linkColor":"#2a2929","linkThickness":2}}],"attr":{"id":""},"config":{"showGrid":true,"showGridText":"隐藏网格","showGridIcon":"eye"},"status":"1","remarks":[]}'
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
