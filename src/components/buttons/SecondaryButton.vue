<template>
    <BaseButton
        :disabled="disabled"
        :class="buttonClass"
        class="text-gray-800 font-medium bg-gray-100"
        @click="handleClick"
    >
        <slot />
    </BaseButton>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue'
import BaseButton from './BaseButton.vue'

export default defineComponent({
    name: 'SecondaryButton',
    components: {
        BaseButton
    },
    props: {
        disabled: {
            type: Boolean,
            default: false
        }
    },
    emits: {
        click: null
    },
    setup(props, { emit }) {
        const handleClick = () => {
            emit('click')
        }

        const buttonClass = computed(() =>
            props.disabled ? 'opacity-50 cursor-not-allowed' : 'hover:opacity-95'
        )

        return {
            handleClick,
            buttonClass
        }
    },
})
</script>
