<template>
  <div class="container mx-auto p-4">
    <div class="flex items-center flex-wrap">
      <NuxtLink class="btn btn-primary" :to="{ name: 'posts' }">Posts</NuxtLink>
      <NuxtLink
        v-if="$route.params.id > 1"
        class="btn btn-secondary ml-2"
        :to="{
          name: 'posts-id',
          params: { id: parseInt($route.params.id) - 1 },
        }"
      >
        Previous
      </NuxtLink>
      <NuxtLink
        v-if="$route.params.id < 100"
        class="btn btn-secondary ml-2 sm:ml-auto"
        :to="{
          name: 'posts-id',
          params: { id: parseInt($route.params.id) + 1 },
        }"
      >
        Next
      </NuxtLink>
    </div>
    <FetchState :state="$fetchState" class="mt-6">
      <PostDetail :post="post" />
    </FetchState>
  </div>
</template>

<script lang="ts">
import {
  computed,
  defineComponent,
  ref,
  useContext,
  useFetch,
  useRoute,
} from "@nuxtjs/composition-api";
import { Context } from "@nuxt/types";

export default defineComponent({
  name: "Post",
  /*
    validate({ params }: Context): Promise<boolean> | boolean {
    return (
      /^\d+$/.test(params.id) &&
      parseInt(params.id) > 0 &&
      parseInt(params.id) <= 100
    );
  },
    */

  setup() {
    const route = useRoute();
    const id = computed(() => route.value.params.id);
    const post = ref({});
    const { $api } = useContext();

    useFetch(async () => {
      post.value = await $api.posts.show({ id: id.value });
    });

    return { post };
  },
});
</script>
