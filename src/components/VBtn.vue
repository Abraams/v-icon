<template>
    <component
        :class="{
            'v-btn' : true,
            'v-btn--block' : block,
            [`v-btn--${color}`] : true
        }"
        :is="tagName"
    >
        <div class="v-btn__content-wrapper">
            <slot />
        </div>

        <div
            v-if="hasIcon"
            :class="[
                'v-btn__icon-wrapper',
                `v-btn__icon-wrapper--${iconPosition}`
            ]"
        >
            <slot
                name="icon"
                :color="iconColor"
            >
                <VIcon
                    :icon="icon"
                    :color="iconColor"
                />
            </slot>
        </div>
    </component>
</template>

<script setup>
import { computed, defineSlots } from "vue";
import VIcon from './VIcon.vue'

const slots = defineSlots()

const props = defineProps({
    tag: {
        type: String,
        default: 'button'
    },
    href: {
        type: String,
        default: null
    },
    icon: {
        type: Object,
        default: null
    },
    iconPosition: {
        type: String,
        default: 'right'
    },
    block: {
        type: Boolean,
        default: false
    },
    color: {
        type: String,
        default: 'blue'
    }
})

const tagName = computed(() => props.href ? 'a' : props.tag)
const hasIcon = computed(() => Boolean(slots.icon || props.icon))
const iconColor = computed(() => {
    const map = {
        'red': 'green',
        'blue': 'red',
        'green': 'blue',
    }

    return map[props.color]
})

</script>

<style>
.v-btn {
    display: inline-flex;
    align-items: center;
}

.v-btn--blue {
    background: blue;
}

.v-btn--green {
    background: green;
}

.v-btn--red {
    background: red;
}

.v-btn--block {
    display: flex;
}

.v-btn__icon-wrapper {
    display: inline-flex;
    align-items: center;
}

.v-btn__icon-wrapper--left {
    order: -1;
}

.v-btn__icon-wrapper--right {
    order: 100;
}

</style>
