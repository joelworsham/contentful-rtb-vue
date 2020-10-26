<template>
  <p>
    <rtb-node
      v-for="(node, nodeI) in content"
      :key="nodeI"
      :node="node"
    />
  </p>
</template>

<script>
export default {
  name: 'RtbNodeParagraph',
  components: { RtbNode: () => import('./rtb-node.vue') },
  props: {
    content: {
      type: Array,
      required: true,
    },
  },
};
</script>
