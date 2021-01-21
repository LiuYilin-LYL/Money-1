<template>
  <Layout>
    <div class="tags">
      <router-link class="tag" :to="`/labels/edit/${tag.id}`" v-for="tag in tags" :key="tag.id">
        <span>{{ tag.name }}</span>
        <Icon name="right"></Icon>
      </router-link>
    </div>
    <div class="creatTag-wrapper">
      <Button class="creatTag" @click="createTag">新建标签</Button>
    </div>
  </Layout>
</template>

<script lang="ts">
import Vue from 'vue';
import {Component} from 'vue-property-decorator';
import tagListModel from '@/models/tagListModel';
import Button from '@/components/Button.vue';

tagListModel.fetch();
@Component({
  components: {Button}
})
export default class Labels extends Vue {
  tags = tagListModel.data;

  createTag() {
    const name = window.prompt('请输入标签名');
    if (name) {
      const message = tagListModel.create(name);
      if (message === 'duplicated') {
        window.alert('标签名已存在');
      } else if (message === 'success')
        window.alert('添加成功');
    }
  }
}
</script>

<style lang="scss" scoped>
.tags {
  font-size: 18px;
  background: darken(#fbecde, 2%);
  padding-left: 16px;

  > .tag {
    min-height: 44px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 1px solid coral;

    svg {
      width: 28px;
      height: 28px;
      color: darksalmon;
      margin-right: 16px;
    }
  }
}

.creatTag {
  background: #fb9968;
  color: #fbecde;
  border-radius: 4px;
  border: none;
  height: 40px;
  padding: 0 16px;

  &-wrapper {
    padding: 40px;
    text-align: center;
  }
}
</style>