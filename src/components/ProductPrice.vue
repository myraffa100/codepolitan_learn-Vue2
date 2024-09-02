<template>
  <span>{{ prefix + Number.parseFloat(value).toFixed(precision) }}</span>
</template>

<script>
export default {
  name: "ProductPrice", // Pastikan nama komponen sesuai dengan aturan
  props: {
    value: {
      type: Number,
      required: true,
    },
    prefix: {
      type: String,
      default: "Rp",
    },
    precision: {
      type: Number,
      default: 2,
    },
  },
};
</script>
