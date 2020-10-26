<template>
  <ul>
    <li
      v-for="(contentItem, contentItemI) in content"
      :key="contentItemI"
    >
      <rtb-node
        v-for="(node, nodeI) in contentItem.content"
        :key="nodeI"
        :node="node"
      />
    </li>
  </ul>
</template>

<script>
export default {
  name: 'RtbNodeUnorderedList',
  components: { RtbNode: () => import('./rtb-node.vue') },
  props: {
    content: {
      type: Array,
      default: undefined,
    },
  },
};
</script>
