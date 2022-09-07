<template>
    <Head title="Create Community" />

    <BreezeAuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Edit Post for {{ community.name }}
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="max-w-md mx-auto bg-white m-2 p-6">
                    <form @submit.prevent="submit">
                        <div>
                            <BreezeLabel for="title" value="Title" />
                            <BreezeInput id="title" type="text" class="mt-1 block w-full" v-model="form.title" autofocus autocomplete="title" />
                            <BreezeInputError class="mt-2" :message="form.errors.title" />
                        </div>

                        <div>
                            <BreezeLabel for="url" value="Url" />
                            <BreezeInput id="url" type="text" class="mt-1 block w-full" v-model="form.url"  autocomplete="url" />
                            <BreezeInputError class="mt-2" :message="form.errors.url" />
                        </div>

                        <div class="mt-4">
                            <BreezeLabel for="description" value="Description" />
                            <BreezeInput id="description" type="text" class="mt-1 block w-full" v-model="form.description" autocomplete="description" />
                            <BreezeInputError class="mt-2" :message="form.errors.description" />
                        </div>

                        <div class="flex items-center justify-end mt-4">
                            <BreezeButton class="ml-4" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                                Update
                            </BreezeButton>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </BreezeAuthenticatedLayout>
</template>

<script setup>
import BreezeInput from '@/Components/Input.vue';
import BreezeInputError from '@/Components/InputError.vue';
import BreezeLabel from '@/Components/Label.vue';
import BreezeButton from '@/Components/Button.vue';
import BreezeAuthenticatedLayout from '@/Layouts/Authenticated.vue';
import { Head, Link, useForm } from '@inertiajs/inertia-vue3';

const props = defineProps({
    post:Object,
    community:Object
});

const form = useForm({
    title: props.post?.title,
    url: props.post?.url,
    description: props.post?.description,
});

const submit = () => {
    form.put(route('communities.posts.update', [props.community.slug, props.post.slug]));
};

</script>
