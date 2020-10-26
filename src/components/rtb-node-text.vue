<template>
  <span>
    <rtb-mark
      v-if="markWithNested"
      :mark="markWithNested"
    >
      {{ value }}
    </rtb-mark>

    <template v-if="!markWithNested">
      {{ value }}
    </template>
  </span>
</template>

<script>
import RtbMark from './rtb-mark.vue';
import nestMarks from '../../util/rich-text-block/nestMarks';

export default {
  name: 'RtbNodeText',
  components: { RtbMark },
  props: {
    marks: {
      type: Array,
      default: undefined,
    },
    value: {
      type: String,
      required: true,
    },
  },
  computed: {
    markWithNested() {
      return nestMarks(this.marks);
    },
  },
};
</script>
