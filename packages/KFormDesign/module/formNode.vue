<!--
 * @Author: kcz
 * @Date: 2019-12-30 00:37:05
 * @LastEditTime: 2020-03-27 19:19:11
 * @LastEditors: kcz
 * @Description: 将数据通过k-form-item组件解析，生成控件
 * @FilePath: \k-form-design\packages\KFormDesign\module\formNode.vue
 -->
<template>
  <div
    class="drag-move-box"
    @click.stop="$emit('handleSelectItem', record)"
    :class="{ active: record.key === selectItem.key }"
  >
    <div class="form-item-box">
      <kFormItem :config="config" :record="record" />
    </div>
    <div class="show-key-box" v-text="record.model" />
    <div
      class="copy"
      :class="record.key === selectItem.key ? 'active' : 'unactivated'"
      @click.stop="$emit('handleCopy')"
    >
      <a-icon type="copy" />
    </div>
    <div
      class="delete"
      :class="record.key === selectItem.key ? 'active' : 'unactivated'"
      @click.stop="$emit('handleDetele')"
    >
      <a-icon type="delete" />
    </div>
  </div>
</template>
<script>
/*
 * author kcz
 * date 2019-11-20
 * description 通过json生成的单个表单节点
 */
import kFormItem from "../../KFormItem/index";
export default {
  props: {
    record: {
      type: Object,
      required: true
    },
    selectItem: {
      type: Object,
      default: () => {}
    },
    config: {
      type: Object,
      required: true
    }
  },
  components: {
    kFormItem
  }
};
</script>
