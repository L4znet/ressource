<template>
    <a @click="save()">
        <slot></slot>
    </a>
</template>

<script>

    export default {
        name: 'Button',
        data() {
            return {
            }
        },
        emits: ['save'],
        methods: {
            save() {
                this.$emit('save', true)
            }
        }
    }
</script>

<style scoped>
    a {
        width: 200px;
        min-height: 50px;
        background-color: rgb(71, 22, 110);
        border-radius: 4px;
        color: #FFF;
        display: flex;
        justify-content: center;
        align-items: center;
        transition: all 0.3s;
        text-decoration: none;
        font-size: 15px;
        margin-top: 20px;
    }

    a:hover {
        background-color: rgb(107, 57, 148);
        transition: all 0.3s;
        cursor: pointer;
    }

</style>
