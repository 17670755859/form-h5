<template>
  <div class="wg-item flex-wrap wg-checkbox" :class="[item.label.labelPosition==='top'?'flex-column':'align-middle']" :style="item.style">
    <div class="wg-title" :style="$util.changeRem(item.label.labelwidth)">{{item.label.labelTitle}}</div>
    <div class="flex-auto">
      <label class="label" v-for="(optionsItem, key) in item.options" :key="optionsItem + key">
        <input class="wg-checkbox-input" :type="item.isRadio?'radio':'checkbox'" :value="optionsItem" v-model="item.value" style="display:none" />
        <span>{{optionsItem}}</span>
      </label>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    item: Object
  },
  methods: {
    validate() {
      if (Array.isArray(this.item.value) && this.item.value.length === 0 || this.item.value === '') return `请选择${this.item.labelTitle}`;
      return true;
    }
  }
}
</script>
