<docs>
---
order: 3
title:
  zh-CN: 可交互
  en-US: Interactive
---

## zh-CN

提供可编辑和可复制等额外的交互能力。

## en-US

Provide additional interactive capacity of editable and copyable.
</docs>
<template>
  <a-typography-paragraph v-model:content="editableStr" editable />
  <a-typography-paragraph v-model:content="customIconStr" editable>
    <template #editableIcon><HighlightOutlined /></template>
    <template #editableTooltip>click to edit text</template>
  </a-typography-paragraph>
  <a-typography-paragraph v-model:content="hideTooltipStr" :editable="{ tooltip: false }" />
  <a-typography-paragraph
    v-model:content="lengthLimitedStr"
    :editable="{ maxlength: 50, autoSize: { maxRows: 5, minRows: 3 } }"
  />

  <a-typography-paragraph copyable>This is a copyable text.</a-typography-paragraph>
  <a-typography-paragraph :copyable="{ text: 'Hello, Ant Design!' }">
    Replace copy text.
  </a-typography-paragraph>
  <a-typography-paragraph copyable content="Custom Copy icon and replace tooltips text.">
    <template #copyableIcon="{ copied }">
      <SmileOutlined v-if="!copied" key="copy-icon" />
      <SmileFilled v-else key="copied-icon" />
    </template>
    <template #copyableTooltip="{ copied }">
      <span v-if="!copied" key="copy-tooltip">click here</span>
      <span v-else key="copied-tooltip">you clicked!!</span>
    </template>
  </a-typography-paragraph>
  <a-typography-paragraph :copyable="{ tooltip: false }">
    Hide Copy tooltips.
  </a-typography-paragraph>
</template>
<script lang="ts">
import { defineComponent, ref, watch } from 'vue';
import { HighlightOutlined, SmileOutlined, SmileFilled } from '@ant-design/icons-vue';

export default defineComponent({
  components: {
    HighlightOutlined,
    SmileOutlined,
    SmileFilled,
  },
  setup() {
    const editableStr = ref('This is an editable text.');
    watch(editableStr, () => {
      console.log('editableStr', editableStr.value);
    });
    return {
      editableStr,
      customIconStr: ref('Custom Edit icon and replace tooltip text.'),
      hideTooltipStr: ref('Hide Edit tooltip.'),
      lengthLimitedStr: ref('This is an editable text with limited length.'),
    };
  },
});
</script>
