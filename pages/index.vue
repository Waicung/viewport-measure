<script setup>
const viewPortSize = ref({ width: 0, height: 0 });
const bodySize = ref({ width: 0, height: 0 });
const componentSize = ref({ width: 0, height: 0 });
const component = ref(null);

onMounted(() => {
  const updateSize = () => {

    document.documentElement.style.setProperty('--vh', `${window.innerHeight * 0.01}px`);
    
    viewPortSize.value = {
      width: window.innerWidth,
      height: window.innerHeight,
    };
    bodySize.value = {
      width: document.body.clientWidth,
      height: document.body.clientHeight,
    };

    componentSize.value = {
      width: component.value.clientWidth,
      height: component.value.clientHeight,
    };  

  };

  window.addEventListener('resize', updateSize);
  updateSize();

});
</script>

<template>
  <div :style="{ height: 'calc(var(--vh, 1vh) * 100)' }"  ref="component">
    <div class="flex items-center justify-center h-screen flex-col bg-green-200">
      <p>ViewPort {{ viewPortSize }}</p>
      <p>100vh Body {{ bodySize }}</p>
      <p>Custom Height Component {{ componentSize }}</p>
    </div>
  </div>
</template>