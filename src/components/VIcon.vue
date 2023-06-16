<template>
    <svg
        class="v-icon"
        xmlns="http://www.w3.org/2000/svg"
        :width="width || icon.width"
        :height="height || icon.height"
        :viewBox="viewBox || icon.viewBox"
        :fill="color"
    >
        <path
            v-for="path in icon.svgPathData"
            :fill-rule="path.fillRule"
            :clip-rule="path.clipRule"
            :d="path.d"
        />
    </svg>
</template>

<script setup>
defineProps({
    width: {
        type: [String, Number],
        default: 24
    },
    height: {
        type: [String, Number],
        default: 24
    },
    viewBox: {
        type: String,
        default: '0 0 24 24'
    },
    color: {
        type: String,
        default: '#333333'
    },
    icon: {
        type: Object,
        required: true
    }
})
</script>
