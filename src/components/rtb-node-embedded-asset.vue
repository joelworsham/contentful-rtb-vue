<template>
  <div class="mb-5">
    <ldc-asset v-bind="target.fields"/>
  </div>
</template>

<script>
import LdcAsset from '../asset/ldc-asset';

export default {
  name: 'RtbNodeEmbeddedAsset',
  components: { LdcAsset },
  props: {
    target: {
      type: Object,
      required: true,
    },
  },
};
</script>
