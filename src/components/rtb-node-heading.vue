<template>
  <component :is="headingTag">
    <rtb-node
      v-for="(node, nodeI) in content"
      :key="nodeI"
      :node="node"
    />
  </component>
</template>

<script>
export default {
  name: 'RtbNodeHeading',
  components: { RtbNode: () => import('./rtb-node.vue') },
  props: {
    content: {
      type: Array,
      required: true,
    },
    level: {
      type: String,
      required: true,
    },
  },
  computed: {
    headingTag() {
      return `h${this.level}`;
    },
  },
};
</script>
