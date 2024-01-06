<script setup>
import { Inertia } from "@inertiajs/inertia";

defineProps({
    id: String,
    blog: Object,
});
const deleteConfirm = (id) => {
    Inertia.delete(`/inertia/${id}`, {
        onBefore: () => confirm("本当に削除しますか？"),
    });
};
</script>

<template>
    <div class="flex justify-center items-center h-screen">
        <div class="w-full max-w-md mx-auto text-center space-y-4">
            <h1 class="text-2xl font-bold mb-6">Blog詳細</h1>

            <div class="mb-4 text-left">
                <label for="title" class="block font-medium">件名:</label>
                <input
                    type="text"
                    id="title"
                    class="border p-2 w-full"
                    :value="blog.title"
                    readonly
                />
            </div>

            <div class="mb-4 text-left">
                <label for="content" class="block font-medium">本文:</label>
                <textarea
                    id="content"
                    class="border p-2 w-full"
                    rows="4"
                    :value="blog.content"
                    readonly
                ></textarea>
            </div>

            <button
                @click="deleteConfirm(blog.id)"
                class="bg-red-500 text-white p-2 rounded hover:bg-red-600"
            >
                削除
            </button>
        </div>
    </div>
</template>
