<template>
  <component :is="markTag">
    <!-- Recursive marks -->
    <rtb-mark
      v-if="mark.nextMark"
      :mark="mark.nextMark"
    >
      <slot/>
    </rtb-mark>

    <!-- End of marks -->
    <slot v-if="!mark.nextMark"/>
  </component>
</template>

<script>
export default {
  name: 'RtbMark',
  props: {
    mark: {
      type: Object,
      required: true,
    },
  },
  computed: {
    markTag() {
      switch (this.mark.type) {
        case 'code':
          return 'code';
        case 'bold':
          return 'strong';
        case 'italic':
          return 'em';
        case 'underline':
          return 'u';
        default:
          throw new Error(`Unrecognized or unsupported mark type: ${this.mark.type}`);
      }
    },
  },
};
</script>
