<template>
    <div class="mt-4 p-2 max-w-4xl flex bg-white rounded-lg border border-gray-200 shadow-md dark:bg-gray-800 dark:border-gray-700">
        <div class="mr-3">upvote</div>
        <div>
            <div class="flex m-2 p-2">
                <span class="font-semibold mr-3">r/{{ community.slug }}</span>
                <div class="flex">
                    Posted By
                    <span class="font-semibold ml-1">{{ post.username }}</span>
                </div>
            </div>
            <a href="">
                <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">{{ post.title }}</h5>
            </a>
            <p class="mb-3 font-normal text-gray-300 dark:text-gray-400">{{ post.description }}</p>
            <div class="flex m-2 p-2">
                <p class="mr-4 p-2">Comments(2)</p>
                <Link :href="route('frontend.communities.post.show',[community.slug, post.slug])" class="inline-flex items-center py-2 px-3 text-sm font-medium text-center text-white bg-blue-500 rounded">
                    Read More
                </Link>
            </div>
        </div>
    </div>
</template>

<script setup>
    import { Link } from '@inertiajs/inertia-vue3';
    defineProps({
        post:Object,
        community:Object,
    });
</script>
