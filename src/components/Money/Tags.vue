<template>
  <div class="tags">
    <div class="new">
      <button @click="create">新增标签</button>
    </div>
    <ul class="current">
      <li v-for="tag in dataSource" :key="tag.id"
          :class="{selected: selectedTags.indexOf(tag)>=0}"
          @click="toggle(tag)">{{tag.name}}
      </li>
    </ul>
  </div>

</template>

<script lang="ts">
import Vue from 'vue';
import {Component, Prop} from 'vue-property-decorator';

@Component
export default class Tags extends Vue {
  @Prop() readonly dataSource: string[] | undefined;
  selectedTags: string[] = [];

  toggle(tag: string) {
    const index = this.selectedTags.indexOf(tag);
    if (index >= 0) {
      this.selectedTags.splice(index, 1);
    } else {
      this.selectedTags.push(tag);
    }
    this.$emit('update:value', this.selectedTags);
  }

  create() {
    const name = window.prompt('请输入标签名');
    if (name === '') {
      window.alert('标签名不能为空');
    } else if (this.dataSource) {
      this.$emit('update:dataSource',
          [...this.dataSource, name]);
    }
  }
}
</script>
<style lang="scss" scoped>
.tags {
  display: flex;
  flex-direction: column-reverse;
  flex-grow: 1;
  font-size: 14px;
  padding: 16px;

  > .current {
    display: flex;
    flex-wrap: wrap;

    > li {
      color: lightyellow;
      background: #f3a683;
      $h: 24px;
      height: $h;
      line-height: $h;
      border-radius: $h/2;
      padding: 0 16px;
      margin-right: 12px;
      margin-top: 4px;

      &.selected {
        background: darken(#f3a683, 12%);
      }
    }
  }

  > .new {
    padding-top: 16px;
    button {
      background: transparent;
      border: none;
      color: #ed556a;
      border-bottom: 1px solid;
      padding: 0 4px;
    }
  }
}
</style>