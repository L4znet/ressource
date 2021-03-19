<template>
    <div class="modal">
        <div class="modal_header">
            <slot name="title"></slot>
        </div>
        <div class="modal_body">
            <slot name="text"></slot>
        </div>
        <div class="modal_footer">
            <slot name="buttons"></slot>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'modal',
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
        components: {
        }
    }
</script>

<style scoped>
    .modal {
        width: 800px;
        height: 200px;
        background-color: #FFF;
        border: 1px solid rgb(218, 218, 218);
        display: flex;
        flex-direction: column;
        position: absolute;
        z-index: 9999;
        top: 20%;
    }

    .modal .modal_header {
        width: 100%;
        min-height: 70px;
        font-size: 24px;
        font-weight: bold;
        background-color: rgb(71, 22, 110);
        display: flex;
        justify-content: center;
        align-items: center;
        color: #FFF;
    }

    .modal .modal_body {
        width: 95%;
        height: 100%;
        font-size: 17px;
        padding: 20px;
    }

    .modal .modal_footer {
        width: 100%;
        height: 90px;
        font-size: 30px;
        display: flex;
        justify-content: flex-end;
    }

</style>
