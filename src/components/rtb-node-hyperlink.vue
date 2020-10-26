<template>
  <lds-link
    :href="uriHref"
    :to="uriTo"
    :external="external"
    :target="target"
  >
    <rtb-node
      v-for="(node, nodeI) in content"
      :key="nodeI"
      :node="node"
    />
  </lds-link>
</template>

<script>
import {
  isExternalLink,
  shouldLinkOpenInNewTab,
} from 'global-ctfl-middleware/lib/ldsContentParsers/links';

export default {
  name: 'RtbNodeHyperlink',
  components: { RtbNode: () => import('./rtb-node.vue') },
  props: {
    content: {
      type: Array,
      default: undefined,
    },
    uri: {
      type: String,
      required: true,
    },
  },
  computed: {
    external() {
      return isExternalLink(this.uri);
    },

    target() {
      return shouldLinkOpenInNewTab(this.uri) ? '_blank' : undefined;
    },

    uriHref() {
      return this.uri.startsWith('http') ? this.uri : undefined;
    },

    uriTo() {
      return this.uri.startsWith('/') ? this.uri : undefined;
    },
  },
};
</script>
