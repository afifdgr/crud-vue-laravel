<script setup>
import { reactive } from "vue";
import useSkills from "../../composables/skills";

const { storeSkill, errors } = useSkills();

const form = reactive({
    name: "",
    slug: "",
});
</script>
<template>
    <div class="mt-12">
        <form class="max-w-md mx-auto p-4 bg-white shadow-md rounded-md" @submit.prevent="storeSkill(form)">
            <div class="space-y-6">
                <div class="mb-6">
                    <label for="name"
                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-black-300">Name</label>
                    <input type="text" id="name" v-model="form.name"
                        class="bg-white-50 border border-green-400 text-white-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-white-700 dark:border-white-600 dark:placeholder-white-400 dark:text-black dark:focus:ring-blue-500 dark:focus:border-blue-500" />
                    <div v-if="errors.name">
                        <span class="text-sm text-red-400">{{ errors.name[0] }}</span>
                    </div>
                </div>
                <div class="mb-6">
                    <label for="slug"
                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-black-300">Slug</label>
                    <input type="text" id="slug" v-model="form.slug"
                        class="bg-white-50 border border-green-400 text-white-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-white-700 dark:border-white-600 dark:placeholder-white-400 dark:text-black dark:focus:ring-blue-500 dark:focus:border-blue-500" />
                    <div v-if="errors.slug">
                        <span class="text-sm text-red-400">{{ errors.slug[0] }}</span>
                    </div>
                </div>
                <div class="mt-4">
                    <button type="submit" class="px-4 py-2 mr-4 bg-green-500 hover:bg-green-700 rounded text-white">
                        Store
                    </button>
                </div>
            </div>
        </form>
    </div>
</template>
