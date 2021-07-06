<template>
  <div>{{ item.name }} {{ item.username }}</div>
</template>
<script>
export default {
  name: "User",
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
};
</script>