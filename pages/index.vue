<script setup>
const viewPortSize = ref({ width: 0, height: 0 });
const bodySize = ref({ width: 0, height: 0 });

onMounted(() => {
  const updateSize = () => {
    viewPortSize.value = {
      width: window.innerWidth,
      height: window.innerHeight,
    };
    bodySize.value = {
      width: document.body.clientWidth,
      height: document.body.clientHeight,
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
    <div class="flex items-center justify-center h-screen flex-col">
      <p>ViewPort{{ viewPortSize }}</p>
      <p>Body{{ bodySize }}</p>
    </div>
  </div>
</template>