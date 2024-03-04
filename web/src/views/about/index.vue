<template>
  <div>
    <div class="n-layout-page-header">
      <n-card :bordered="false" title="关于">
        咕嘟AI助手 官方客服QQ: 1226325290。
      </n-card>
    </div>
    <n-card
      :bordered="false"
      title="项目信息"
      class="mt-4 proCard"
      size="small"
      :segmented="{ content: true }"
    >
      <n-descriptions bordered label-placement="left" class="py-2">
        <n-descriptions-item label="咕嘟AI助手版本">
          <n-tag type="info"> {{ config?.version }}</n-tag>
        </n-descriptions-item>
        <n-descriptions-item label="最后编译时间">
          <n-tag type="info"> {{ lastBuildTime }} </n-tag>
        </n-descriptions-item>
        <n-descriptions-item label="QQ交流群">
          <div class="flex items-center">
            <a href="https://qm.qq.com/q/gOhIO4EQVy" class="py-2" target="_blank"
              >点击链接加入群聊【咕嘟AI助手 交流群】</a
            >
          </div>
        </n-descriptions-item>
      </n-descriptions>
    </n-card>
  </div>
</template>

<script lang="ts" setup>
  import { ref } from 'vue';
  import { useUserStoreWidthOut } from '@/store/modules/user';

  const useUserStore = useUserStoreWidthOut();
  const config = ref(useUserStore.config);
  export interface schemaItem {
    field: string;
    label: string;
  }

  const { pkg, lastBuildTime } = __APP_INFO__;
  const { dependencies, devDependencies, name } = pkg;

  const schema: schemaItem[] = [];
  const devSchema: schemaItem[] = [];

  Object.keys(dependencies).forEach((key) => {
    schema.push({ field: key, label: dependencies[key] });
  });

  Object.keys(devDependencies).forEach((key) => {
    devSchema.push({ field: key, label: devDependencies[key] });
  });
</script>

<style lang="less" scoped></style>
