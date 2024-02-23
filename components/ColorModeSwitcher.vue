<script setup lang="ts">
    const colorMode = useColorMode()
    const modes = ['system', 'light', 'dark']
    const index = ref(modes.indexOf(colorMode.value))
    const hovered = ref(false)

    console.log(colorMode.value)

    const handleSwitchColorMode = () => {
        if(index.value === modes.length-1) {
            index.value = 0
        } else {
            index.value ++
        }
        colorMode.value = modes[index.value]
    }
    
</script>

<template>
    <div class="flex items-center">
            <p v-show="hovered === true" class="flex transition-all ease-in-out">{{ colorMode.value }} </p>
            <UButton variant="ghost"  v-if="colorMode.value === 'light'" @mouseover="hovered = true" @mouseleave="hovered = false"  @click="handleSwitchColorMode"> 🌕  </UButton>
            <UButton variant="ghost"  v-else-if="colorMode.value === 'dark'" @mouseover="hovered = true" @mouseleave="hovered = false" @click="handleSwitchColorMode"> 🌚  </UButton>
            <UButton variant="ghost"  v-else-if="colorMode.value === 'system'" @mouseover="hovered = true" @mouseleave="hovered = false" @click="handleSwitchColorMode"> 🌗  </UButton>
    </div>

</template>