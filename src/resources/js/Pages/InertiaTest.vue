<script setup>
import { Link } from "@inertiajs/inertia-vue3";
import { ref } from "vue";

const newTitle = ref("");
const newContent = ref("");
</script>

<template>
    <div class="flex flex-col justify-center items-center h-screen">
        <div class="text-center">
            <h1 class="text-2xl font-bold mb-4">Inertia一覧</h1>

            inertiaテスト<br />
            <a href="/">aタグ経由です</a><br />
            <Link href="/">Link経由です</Link><br />
            <Link :href="route('inertia.index')">名前付きルートの確認です</Link
            ><br />
            <Link :href="route('inertia.show', { id: 1 })"
                >ルートパラメータのテストです</Link
            ><br />

            <div class="mb-8"></div>
            <input
                type="text"
                name="newTitle"
                v-model="newTitle"
                class="border p-2"
            />{{ newTitle }}<br />
            <input
                type="text"
                name="newContent"
                v-model="newContent"
                class="border p-2"
            />{{ newContent }}<br />
            <Link
                as="button"
                method="post"
                :href="route('inertia.store')"
                :data="{
                    title: newTitle,
                    content: newContent,
                }"
                class="bg-blue-500 text-white p-2 rounded mt-4"
                >DB保存テスト</Link
            >
        </div>
    </div>
</template>
