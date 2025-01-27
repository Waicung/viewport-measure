<script setup>
const viewPortSize = ref({ width: 0, height: 0 });

onMounted(() => {
  const updateSize = () => {
    viewPortSize.value = {
      width: window.innerWidth,
      height: window.innerHeight,
    };
  };

  window.addEventListener('resize', updateSize);
  updateSize();

  return () => {
    window.removeEventListener('resize', updateSize);
  };
});
</script>

<template>
  <div class="">
    <div class="flex items-center justify-center h-screen">
      <text class="text-center">
      {{ viewPortSize }}
      </text>
    </div>
  </div>
</template>