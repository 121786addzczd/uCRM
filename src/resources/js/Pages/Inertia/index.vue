<script setup>
import { Link } from "@inertiajs/inertia-vue3";

defineProps({
    blogs: Array,
});
</script>

<template>
    <div class="flex flex-col items-center">
        <div
            v-if="$page.props.flash.message"
            class="bg-green-300 p-3 rounded my-4 w-full max-w-md"
        >
            {{ $page.props.flash.message }}
        </div>

        <h1 class="text-2xl font-bold mb-4">blog一覧</h1>

        <ul class="w-full max-w-md">
            <li
                v-for="(blog, index) in blogs"
                :key="blog.id"
                class="border-b border-gray-200 py-2"
            >
                <span class="font-semibold">{{ index + 1 }}. 件名: </span>
                <Link
                    class="text-blue-400 hover:text-blue-600"
                    :href="route('inertia.show', { id: blog.id })"
                    >{{ blog.title }}</Link
                >,
                <span class="font-semibold">本文: </span>
                {{ blog.content }}
            </li>
        </ul>
    </div>
</template>
