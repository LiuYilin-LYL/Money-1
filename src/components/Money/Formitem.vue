<template>
  <div>
    <label class="formItem">
      <span class="name">{{this.fieldName}}</span>
      <input type="text" :value="value"
             @input="onValueChanged($event.target.value)"
            :placeholder="this.placeholder">
    </label>
  </div>
</template>


<script lang="ts">
import Vue from 'vue';
import {Component, Prop, Watch} from 'vue-property-decorator';

@Component
export default class FormItem extends Vue {
@Prop({default:''}) value!: string;
@Prop({required:true}) fieldName!: string;
@Prop()placeholder?: string

@Watch("value")
onValueChanged(value: string){
this.$emit("update:value",value)
}
}
</script>

<style lang="scss" scoped>
.formItem{
  font-size: 14px;
  background: rgba(243, 166, 131, 0.55);
  padding-left: 16px;
  display: flex;
  align-items: center;

.name {
  padding-right: 16px;
}

input {
  height: 40px;
  flex-grow: 1;
  border: none;
  background: transparent;
  padding-right: 16px;
}
}
</style>