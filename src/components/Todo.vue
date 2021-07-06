<template><div>
  <input type="checkbox" :checked="item.completed" />
  {{ item.title }}
  </div>
</template>
<script>
export default {
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
};
</script>