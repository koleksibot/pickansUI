<template>
  <div class="rounded-md my-3 p-4 max-w-xl w-full mx-auto">
    <div class="animate-pulse flex space-x-4">
      <div class="rounded-full bg-blue-400 h-12 w-12"></div>
      <div class="flex-1 space-y-4 py-1">
        <div class="h-4 bg-blue-400 rounded w-3/4"></div>
        <div class="space-y-2">
          <div class="h-4 bg-blue-400 rounded"></div>
          <div class="h-4 bg-blue-400 rounded w-5/6"></div>
          <div class="h-4 bg-blue-400 rounded w-5/6"></div>
          <div class="h-4 bg-blue-400 rounded"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PlaceHolderLoading",
};
</script>
