<template>
  <div>
    <div class="blocklyDiv" ref="blocklyDiv"></div>
    <xml ref="blocklyToolbox" style="display: none">
      <slot></slot>
    </xml>
  </div>
</template>

<script>
import Blockly from "blockly";

//设置Blockly语言为中文
import hans from "blockly/msg/zh-hans";
Blockly.setLocale(hans);

export default {
  name: "BlocklyComponent",
  props: ["options"],
  data() {
    return {
      workspace: null,
    };
  },
  mounted() {
    var options = this.$props.options || {};
    if (!options.toolbox) {
      options.toolbox = this.$refs["blocklyToolbox"];
    }
    this.workspace = Blockly.inject(this.$refs["blocklyDiv"], options);
  },
};
</script>

<style scoped>
.blocklyDiv {
  height: 100%;
  width: 100%;
  text-align: left;
}
</style>
