<script setup lang="ts">
import { ref } from 'vue';
import { Bars3Icon, XMarkIcon } from '@heroicons/vue/24/outline'

const navigation = [
    { name: 'Сотрудники', href: '#' },
    { name: 'Пополнение', href: '#' },
    { name: 'Настройки', href: '#' },
    { name: 'Отчёты', href: '#' },
]

const mobileMenuOpen = ref(false);

</script>

<template>
    <header class="bg-black">
        <nav class="max-w-[1470px] mx-auto flex items-center justify-between p-3 lg:px-8">
            <div class="flex items-center lg:gap-x-16">
                <div class="flex lg:flex-1">
                    <a href="#" class="-m-1.5 p-1.5">
                        <span class="text-white text-[26px]">СУП</span>
                    </a>
                </div>
                <div class="hidden lg:flex lg:gap-x-8">
                    <a v-for="item in navigation" :key="item.name" :href="item.href" :title="item.name" class="text-base font-medium text-[#E6E6E6] lg:hover:text-white lg:hover:font-bold lg:before:block before:content-[attr(title)] before:font-bold before:h-0 before:overflow-hidden before:invisible">{{ item.name }}</a>
                </div>
            </div>
            <div class="flex lg:hidden">
                <button type="button" class="-m-2.5 inline-flex items-center justify-center rounded-md p-2.5 text-gray-700" @click="mobileMenuOpen = true">
                    <Bars3Icon class="h-8 w-8 text-white" aria-hidden="true" />
                </button>
            </div>
            <div class="hidden lg:flex lg:items-center lg:gap-x-6">
                <span class="text-base font-medium text-white">1 209 654 руб.</span>
                <a href="#">
                    <img src="../assets/img/user.png" alt="User image">
                </a>
            </div>
        </nav>
        <Dialog as="div" class="lg:hidden" @close="mobileMenuOpen = false" :open="mobileMenuOpen">
            <div class="fixed inset-0 z-10" />
            <DialogPanel class="fixed inset-y-0 right-0 z-10 w-full overflow-y-auto bg-white px-6 py-6 sm:max-w-sm sm:ring-1 sm:ring-gray-900/10">
                <div class="flex items-center justify-between">
                    <a href="#" class="-m-1.5 p-1.5">
                        <span class="text-black font-bold text-[26px]">СУП</span>
                    </a>
                    <button type="button" class="-m-2.5 rounded-md p-2.5 text-gray-700" @click="mobileMenuOpen = false">
                        <XMarkIcon class="h-8 w-8 text-black" aria-hidden="true" />
                    </button>
                </div>
                <div class="mt-6">
                    <div class="-my-6 divide-y divide-gray-500/10">
                        <div class="space-y-2 py-6">
                            <a v-for="item in navigation" :key="item.name" :href="item.href" class="-mx-3 block rounded-lg px-3 py-2 text-lg font-semibold leading-7 text-black">{{ item.name }}</a>
                        </div>
                        <div class="pt-4 flex items-center gap-x-6">
                            <a href="#">
                                <img class="h-10 w-10 rounded-full" src="../assets/img/user.png" alt="User image">
                            </a>
                            <span class="text-lg font-medium text-black">1 209 654 руб.</span>
                        </div>
                    </div>
                </div>
            </DialogPanel>
        </Dialog>
    </header>
</template>