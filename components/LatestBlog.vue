<template>
    <div class="bg-white py-24 pt-12 sm:pt-16 sm:py-32">
        <div class="mx-auto max-w-7xl px-6 lg:px-8">
            <div class="mx-auto max-w-2xl lg:mx-0">
                <h2 class="text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl">Latest posts</h2>
                <p class="mt-2 text-lg leading-8 text-gray-600">Stay up to date with the latest developments.</p>
            </div>
            <div class="mx-auto mt-5 grid max-w-2xl grid-cols-1 gap-x-8 gap-y-10 border-t border-gray-200 pt-5 sm:mt-10 sm:pt-10 lg:mx-0 lg:max-w-none lg:grid-cols-3">
                <ContentQuery path="/blog" :limit="3" :sort="{ date: -1 }">
                    <template #default="{ data }">
                        <article v-for="post in data" :key="post._path" class="flex max-w-xl flex-col items-start justify-between">
                            <div class="flex items-center gap-x-4 text-xs">
                                <time :datetime="post.date" class="text-gray-500">{{ post.date }}</time>
                                <span class="relative z-10 rounded-full bg-gray-50 px-3 py-1.5 font-medium text-gray-600 hover:bg-gray-100">
                                    {{ post.category }}
                                </span>
                            </div>
                            <div class="group relative">
                                <h3 class="mt-3 text-lg font-semibold leading-6 text-gray-900 group-hover:text-gray-600">
                                    <a :href="post._path">
                                        <span class="absolute inset-0" />
                                        {{ post.title }}
                                    </a>
                                </h3>
                                <p class="mt-5 line-clamp-3 text-sm leading-6 text-gray-600">{{ post.description }}</p>
                            </div>
                            <div class="relative mt-8 flex items-center gap-x-4">
                                <img :src="authors[post.author].profileUrl" alt="" class="h-10 w-10 rounded-full bg-gray-50" />
                                <div class="text-sm leading-6">
                                    <p class="font-semibold text-gray-900">
                                        <span class="absolute inset-0" />
                                        {{ authors[post.author].fullName }}
                                    </p>
                                    <p class="text-gray-600">{{ authors[post.author].role }}</p>
                                </div>
                            </div>
                        </article>
                    </template>
                </ContentQuery>
            </div>
        </div>
    </div>
</template>

<script setup>
import authors from '../authors.json'
</script>