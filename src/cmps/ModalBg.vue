<template>
    <section @click="close" class="modal-bg">
        <span @click.stop>
            <slot></slot>
        </span>
        
        <span
        class="svg-icon btn exit"
        v-html="$svg('exit')"></span>
    </section>
</template>

<script>
export default {
    props: {
        closeAction: {
            type: String,
            default: 'home'
        }
    },
    methods: {
     close() {
        if (this.closeAction === 'home') this.$router.push('/')
        else this.$emit('closed')
     },
    },
    components: {
    }
}
</script>

<style lang="scss">

</style>