<template lang="pug">            
div
  h2 {{ title }}
  slot
    
</template>

<script lang="ts">
export default defineComponent({
  props: {
    title: {
      type: String,
      default: "Admin Dashboard",
    },
  },

  setup() {
    return {};
  },
});
</script>

<style lang="scss" scoped></style>
