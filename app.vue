<template>
  <div>
    <main class="font-mono wcao bg-base-100">
      <NuxtLoadingBar ref="loadingRef" />
      <NuxtLayout>
        <NuxtPage />
      </NuxtLayout>

      <div class="hiddle lg:block">
        <CoreNextImg />
      </div>
    </main>
  </div>
</template>

<script setup>
const router = useRouter();

const loadingRef = ref(null);

router.beforeEach((_to, _from, next) => {
  loadingRef.value.start();

  if (_to.name.includes("introduce")) {
    setTimeout(next, 300);
  } else {
    next();
  }
});
</script>

<style lang="postcss">
img[lazy="loaded"] {
  animation: imgLoaded 1s;
}

@keyframes imgLoaded {
  0% {
    opacity: 0.1;
  }
  100% {
    opacity: 1;
  }
}
</style>
