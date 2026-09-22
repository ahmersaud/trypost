<script setup lang="ts">
import { usePage } from '@inertiajs/vue3';
import { computed } from 'vue';

import LocaleSwitcher from '@/components/LocaleSwitcher.vue';
import type { Auth } from '@/types';

defineProps<{
    title?: string;
    description?: string;
}>();

const page = usePage();

const isGuest = computed(() => !(page.props.auth as Auth).user);
</script>

<template>
    <div class="grid min-h-svh grid-cols-1 lg:grid-cols-2">
        <div class="flex min-w-0 flex-col gap-4 p-6 md:p-10">
            <div class="flex items-start justify-between gap-4">
                <img
                    src="/images/trypost/logo-light.png?v=apptech-1"
                    alt="Apptech Social"
                    class="h-7 w-auto"
                />

                <LocaleSwitcher v-if="isGuest" />
            </div>

            <div class="flex flex-1 items-center justify-center">
                <div class="w-full max-w-lg">
                    <div class="flex flex-col gap-6">
                        <div class="flex flex-col items-center gap-2 text-center">
                            <h1 v-if="title" class="text-2xl font-bold">
                                {{ title }}
                            </h1>
                            <p
                                v-if="description"
                                class="text-sm text-balance text-muted-foreground"
                            >
                                {{ description }}
                            </p>
                        </div>

                        <slot />
                    </div>
                </div>
            </div>
        </div>

        <div
            class="relative hidden overflow-hidden border-l-2 border-foreground bg-accent lg:block"
        >
            <div
                class="pointer-events-none absolute -top-24 -right-24 size-[440px] rounded-full bg-violet-200/50 blur-3xl"
            />
            <div
                class="pointer-events-none absolute -bottom-32 -left-32 size-[440px] rounded-full bg-fuchsia-200/40 blur-3xl"
            />

            <div
                class="pointer-events-none absolute inset-0 opacity-[0.06]"
                style="background-image: radial-gradient(circle, #0a0a0a 1px, transparent 1px); background-size: 28px 28px;"
            />

            <div class="relative flex h-full items-center justify-center px-12 xl:px-16">
                <div class="w-full max-w-lg">
                    <div
                        class="mb-6 inline-flex rounded-full border-2 border-foreground bg-white px-4 py-2 text-xs font-bold tracking-wider uppercase shadow-sm"
                    >
                        Apptech Social
                    </div>

                    <h2 class="text-4xl font-bold leading-tight text-foreground xl:text-5xl">
                        Manage your social presence from one place.
                    </h2>

                    <p class="mt-5 max-w-md text-base leading-relaxed text-foreground/70">
                        Connect your social accounts, create and schedule content,
                        and manage publishing across your channels.
                    </p>

                    <div class="mt-10 grid grid-cols-1 gap-4 xl:grid-cols-3">
                        <div class="rounded-xl border-2 border-foreground bg-card p-5 shadow-sm">
                            <div class="font-bold">Connect accounts</div>
                            <p class="mt-2 text-sm text-muted-foreground">
                                Bring your social channels together.
                            </p>
                        </div>

                        <div class="rounded-xl border-2 border-foreground bg-card p-5 shadow-sm">
                            <div class="font-bold">Plan content</div>
                            <p class="mt-2 text-sm text-muted-foreground">
                                Create and schedule posts ahead of time.
                            </p>
                        </div>

                        <div class="rounded-xl border-2 border-foreground bg-card p-5 shadow-sm">
                            <div class="font-bold">Publish</div>
                            <p class="mt-2 text-sm text-muted-foreground">
                                Manage publishing from one workspace.
                            </p>
                        </div>
                    </div>

                    <p class="mt-10 text-sm font-medium text-foreground/60">
                        Built and operated by Apptech Private Limited
                    </p>
                </div>
            </div>
        </div>
    </div>
</template>
