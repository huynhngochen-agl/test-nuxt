<template>
    <div class="tab_container">
    <slot></slot>
    </div>
</template>

<script>
export default {
    name: 'component-tabs',
    data() {
        return {

        }
    },
    props: {
        title: String,
    }
}
</script>