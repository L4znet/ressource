<template>
    <a class="button_modal">
        <slot></slot>
    </a>
</template>

<script>

    export default {
        name: 'Modal',
        data() {
            return {
            }
        },
        emits: ['save'],
        methods: {
            save() {
                this.$emit('save', true)
            }
        },
        props: ['type']
    }
</script>

<style scoped>
    .button_modal {
        width: 170px;
        height: 50px;
        border-radius: 4px;
        font-size: 16px;
        margin-right: 20px;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-bottom: 20px;
    }

    .cancel_btn {
        color: #000;
        background-color: rgb(224, 224, 224);
        transition: all 0.3s;
    }

    .cancel_btn:hover {
        background-color: rgb(230, 230, 230);
        transition: all 0.3s;
        cursor: pointer;
    }

    .confirm_btn {
        color: #FFF;
        background-color: rgb(71, 22, 110);
        transition: all 0.3s;
    }

    .confirm_btn:hover {
        background-color: rgb(107, 57, 148);
        transition: all 0.3s;
        cursor: pointer;
    }

</style>
