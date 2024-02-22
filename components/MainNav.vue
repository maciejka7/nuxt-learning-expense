<template>
    <UHorizontalNavigation :links="links" class="border-b border-gray-200 dark:border-gray-800" />
</template>

<script setup lang="ts">

import type { HorizontalNavigationLink } from '#ui/types'


const links: HorizontalNavigationLink[][] = [
    [
        {
            label: 'Profile',
            avatar: {
                src: 'https://avatars.githubusercontent.com/u/18124391?v=4',
            },
        },
        {
            label: 'Home',
            icon: 'i-heroicons-home',
            to: '/',
        },
        {
            label: 'Expenses',
            icon: 'i-ph-money-light',
            to: "/expenses"
        },
        {
            label: "Income",
            icon: 'i-majesticons-money-plus-line',
            to: '/income'
        },
        {
            label: 'Stats',
            icon: 'i-heroicons-chart-bar',
            to: `/stats`,
        },
        {
            label: 'About',
            icon: 'i-heroicons-information-circle',
            to: '/about',
        },
    ],
];
</script>

<style lang="scss" scoped></style>