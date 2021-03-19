<template>
    <div class="container">
        <div class="side">
            <h3>{{ data.title }}</h3>
            <p>{{ data.description }}</p>
            <a :href="data.link">Voir</a>
        </div>
        <div class="side">
            <a href="" @click.prevent="deleteItem()">Delete</a>
        </div>
    </div>
    <modal v-if="deleteConfirm">
        <template v-slot:title>
            Nous avons besoin de votre confirmation
        </template>
        <template v-slot:text>
            <p>Êtes-vous sûr de vouloir supprimer cet élément ?</p>
        </template>
        <template v-slot:buttons>
            <button-modal @click="confirmDeleteItem()" :class="{confirm_btn: confirm}">Oui !</button-modal>
            <button-modal @click="cancelDeleteItem()" :class="{cancel_btn: cancel}">Non, retour arrière !</button-modal>
        </template>
    </modal>
</template>

<script>
    import ButtonModal from './modal/ButtonModal'
    import Modal from './modal/Modal'
    export default {
        name: 'element-list',
        data() {
            return {
                confirm: true,
                cancel: true,
                deleteConfirm: false
            }
        },
        props: ['data'],
        components: {
            Modal,
            ButtonModal
        },
        emits: ['deleteEvent'],
        methods: {
            deleteItem() {
                this.deleteConfirm = true
            },

            confirmDeleteItem() {
                this.$emit('deleteEvent')
                this.deleteConfirm = false
            },

            cancelDeleteItem() {
                this.deleteConfirm = false
            }
        }
    }
</script>

<style scoped>
    .container {
        width: 500px;
        height: 90px;
        background-color: #FFF;
        border-radius: 4px;
        display: flex;
        margin-top: 30px;
        padding: 20px;
    }

    .container .side:first-child {
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: space-around;
        flex-direction: column;
    }

    .container .side:first-child h3 {
        font-size: 25px;
    }

    .container .side:first-child p {
        font-size: 15px;
    }

    .container .side:first-child a {
        color: orange;
        text-decoration: none;
    }

    .container .side:last-child {
        width: 100px;
        height: 100%;
        display: flex;
        justify-content: flex-end;
        align-items: flex-start;
    }

    .container .side:last-child a {
        color: rgb(228, 52, 42);
        text-decoration: none;
        padding: 10px 20px;
        border-radius: 4px;
    }

    .container .side:last-child a:hover {
        color: rgb(228, 52, 42);
        text-decoration: none;
        background-color: rgb(243, 199, 197);
    }

</style>
