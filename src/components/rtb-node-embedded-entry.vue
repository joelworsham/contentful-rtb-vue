<template>
  <component
    :is="componentName"
    v-bind="target.fields"
    class="mb-5"
  />
</template>

<script>
import { contentfulEntryToVueComponent } from '../../services';

export default {
  name: 'RtbNodeEmbeddedEntry',
  props: {
    target: {
      type: Object,
      required: true,
    },
  },
  computed: {
    componentName() {
      return contentfulEntryToVueComponent(this.target);
    },
  },
};
</script>
