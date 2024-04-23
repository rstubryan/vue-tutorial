<script setup>
// 11
const props = defineProps({
  msg: String,
});

// 12
const emit = defineEmits(["response"]);
emit("response", "hello from child");
</script>

<template>
  <h2>A Child Component!</h2>
  <h4>{{ msg || "No props passed yet" }}</h4>
  <slot>Fallback content</slot>
</template>
