<template>
  <a-form-item :colon="false" :label-col="labelCol" :wrapper-col="wrapperCol" style="margin-bottom:20px;">
    <span slot="label"><img v-if="fill" src="/assets/Vector.svg"/> {{ label }} </span>
    <slot><a-input :maxlength="maxlength" v-decorator="[field, { rules: [{ whitespace: true, required: true, message: label + ' can not be empty.'}] }]"/></slot>
    <a-tooltip v-if="showTip" placement="right" :mouseEnterDelay="0.4" :mouseLeaveDelay="0.4">
      <p slot="title" v-html="tip"></p>
      <a class="tip" href="#"><a-icon type="exclamation-circle" /></a>
    </a-tooltip>
  </a-form-item>
</template>
<script>

export default {
  data () {
    return {
      labelCol: { lg: { span: 8 }, sm: { span: 8 } },
      wrapperCol: { lg: { span: 7 }, sm: { span: 7 } }
    }
  },
  name: 'OmForm',
  props: {
    label: {
      type: String,
      default: ''
    },
    fill: {
      type: Boolean,
      default: true
    },
    field: {
      type: String,
      default: ''
    },
    tip: {
      type: String,
      default: ''
    },
    showTip: {
      type: Boolean,
      default: true
    },
    maxlength: {
      type: Number,
      default: 1000
    }
  }
}
</script>
<style lang="less" scoped>
img {
margin-right:6px;margin-top:-5px;
}
.tip {
  position: absolute;
  margin-left: 8px;
}
</style>
