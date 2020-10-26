<template>
  <div>
    <rtb-node
      v-for="(node, nodeI) in content"
      :key="nodeI"
      :node="node"
    />
  </div>
</template>

<script>
export default {
  name: 'RtbNodeDocument',
  components: { RtbNode: () => import('./rtb-node.vue') },
  props: {
    content: {
      type: Array,
      required: true,
    },
  },
};
</script>
