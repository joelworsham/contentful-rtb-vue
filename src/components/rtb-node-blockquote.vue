<template>
  <lds-blockquote class="mb-5">
    <rtb-node
      v-for="(node, nodeI) in content"
      :key="nodeI"
      :node="node"
    />
  </lds-blockquote>
</template>

<script>
export default {
  name: 'RtbNodeBlockquote',
  components: { RtbNode: () => import('./rtb-node.vue') },
  props: {
    content: {
      type: Array,
      required: true,
    },
  },
};
</script>
