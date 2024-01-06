<script setup>
import { reactive } from "vue";
import { Inertia } from "@inertiajs/inertia";

defineProps({
    errors: Object,
});

const form = reactive({
    title: null,
    content: null,
});

const submitFunction = () => {
    Inertia.post("/inertia", form);
};
</script>

<template>
    <div class="flex justify-center items-center h-screen">
        <form
            @submit.prevent="submitFunction"
            class="space-y-4 w-full max-w-md mx-auto text-center"
        >
            <h1 class="text-2xl font-bold mb-6">Inertia登録画面</h1>

            <div class="mb-4 text-left">
                <div class="flex items-center mb-2">
                    <label for="title" class="font-medium mr-2"
                        >タイトル:</label
                    >
                    <span
                        class="bg-red-500 text-white text-sm px-1 py-0.5 rounded"
                        >必須</span
                    >
                </div>
                <input
                    type="text"
                    id="title"
                    name="title"
                    v-model="form.title"
                    class="border p-2 w-full"
                />
                <div v-if="errors.title" class="text-red-500">
                    {{ errors.title }}
                </div>
            </div>

            <div class="mb-4 text-left">
                <div class="flex items-center mb-2">
                    <label for="content" class="font-medium mr-2">本文:</label>
                    <span
                        class="bg-red-500 text-white text-sm px-1 py-0.5 rounded"
                        >必須</span
                    >
                </div>
                <textarea
                    id="content"
                    name="content"
                    v-model="form.content"
                    class="border p-2 w-full"
                    rows="4"
                ></textarea>
                <div v-if="errors.content" class="text-red-500">
                    {{ errors.content }}
                </div>
            </div>

            <button class="bg-blue-500 text-white p-2 rounded">送信</button>
        </form>
    </div>
</template>
