<template>
  <div class="frame bg-white shadow-xs max-w-lg mx-auto rounded-lg flex flex-col">
    <router-view />

  </div>
</template>

<style lang="scss">
.frame {
  height: 95vh;
  margin: {
    top: 2.5vh;
    bottom: 2vh;
  };
  overflow-y:hidden
}
</style>
