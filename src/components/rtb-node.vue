<template>
  <rtb-node-embedded-asset
    v-if="nodeType === 'embedded-asset'"
    :target="node.data.target"
  />
  <rtb-node-blockquote
    v-else-if="nodeType === 'blockquote'"
    :content="node.content"
  />
  <rtb-node-document
    v-else-if="nodeType === 'document'"
    :content="node.content"
  />
  <rtb-node-embedded-entry
    v-else-if="nodeType === 'embedded-entry'"
    :target="node.data.target"
  />
  <rtb-node-heading
    v-else-if="nodeType === 'heading'"
    :content="node.content"
    :level="getHeadingLevel()"
  />
  <rtb-node-hr v-else-if="nodeType === 'hr'"/>
  <rtb-node-hyperlink
    v-else-if="nodeType === 'hyperlink'"
    :content="node.content"
    :uri="node.data.uri"
  />
  <rtb-node-ordered-list
    v-else-if="nodeType === 'ordered-list'"
    :content="node.content"
  />
  <rtb-node-paragraph
    v-else-if="nodeType === 'paragraph'"
    :content="node.content"
  />
  <rtb-node-text
    v-else-if="nodeType === 'text'"
    :marks="node.marks"
    :value="node.value"
  />
  <rtb-node-unordered-list
    v-else-if="nodeType === 'unordered-list'"
    :content="node.content"
  />
</template>

<script>
import RtbNodeEmbeddedAsset from './rtb-node-embedded-asset.vue';
import RtbNodeBlockquote from './rtb-node-blockquote.vue';
import RtbNodeDocument from './rtb-node-document.vue';
import RtbNodeEmbeddedEntry from './rtb-node-embedded-entry.vue';
import RtbNodeHeading from './rtb-node-heading.vue';
import RtbNodeHr from './rtb-node-hr.vue';
import RtbNodeHyperlink from './rtb-node-hyperlink.vue';
import RtbNodeOrderedList from './rtb-node-ordered-list.vue';
import RtbNodeParagraph from './rtb-node-paragraph.vue';
import RtbNodeText from './rtb-node-text.vue';
import RtbNodeUnorderedList from './rtb-node-unordered-list.vue';

const getNodeComponentType = (nodeType) => {
  if (nodeType.includes('heading-')) return 'heading';
  if (nodeType.includes('embedded-entry-')) return 'embedded-entry';
  if (nodeType.includes('embedded-asset-')) return 'embedded-asset';
  return nodeType;
};

export default {
  name: 'RtbNode',
  components: {
    RtbNodeEmbeddedAsset,
    RtbNodeBlockquote,
    RtbNodeDocument,
    RtbNodeEmbeddedEntry,
    RtbNodeHeading,
    RtbNodeHr,
    RtbNodeHyperlink,
    RtbNodeOrderedList,
    RtbNodeParagraph,
    RtbNodeText,
    RtbNodeUnorderedList,
  },
  props: {
    node: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      nodeType: getNodeComponentType(this.node.nodeType),
    };
  },
  methods: {
    getHeadingLevel() {
      return this.node.nodeType.slice(8);
    },
  },
};
</script>
