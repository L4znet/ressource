<template>
    <section>
        <form action="" v-if="isDataNotSent">
            <label>Title</label>
            <input type="text" v-model="title">
            <label>Description</label>
            <textarea name="" id="" cols="30" rows="10" v-model="description"></textarea>
            <label>Lien</label>
            <input type="text" v-model="link">
            <Button @save="save">Save</Button>
        </form>
        <modal v-if="mustDisplay">
            <template v-slot:title>
                Une erreur a été rencontrée
            </template>
            <template v-slot:text>
                <p>Vous devez remplir tous les champs.</p>
            </template>
            <template v-slot:buttons>
                <button-modal @click="confirmBtn()" :class="{confirm_btn: confirm}">Ok, j'ai compris</button-modal>
            </template>
        </modal>
    </section>
</template>

<script>
    import Button from './Button.vue'
    import ButtonModal from './modal/ButtonModal'
    import Modal from './modal/Modal'
    export default {
        name: 'Form',
        data() {
            return {
                title: this.title,
                description: this.description,
                link: this.link,
                data: {
                    title: '',
                    description: '',
                    link: ''
                },
                confirm: true,
                cancel: true,
                mustDisplay: false,
                isDataNotSent: true
            }
        },
        components: {
            Button,
            Modal,
            ButtonModal
        },
        methods: {
            cleaner() {
                this.title = ''
                this.description = ''
                this.link = ''
            },
            save() {
                if (this.title !== undefined && this.description !== undefined && this.link !== undefined) {
                    this.data.title = this.title
                    this.data.description = this.description
                    this.data.link = this.link

                    this.cleaner()
                    this.isDataNotSent = false
                    this.$emit('saved', this.data)
                } else {
                    this.displayOrNotModal(true)
                }
            },
            confirmBtn() {
                this.displayOrNotModal(false)
            },

            displayOrNotModal(mustDisplay) {
                this.mustDisplay = mustDisplay
            }
        }
    }
</script>

<style scoped>
    form {
        display: flex;
        flex-direction: column;
        background-color: #FFF;
        width: 500px;
        padding: 20px;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-top: 20px;
    }

    form label {
        display: flex;
        width: 83%;
        flex-direction: column;
        font-weight: bold;
        margin-top: 20px;
    }

    form input {
        border: 1px solid rgb(218, 218, 218);
        width: 400px;
        height: 30px;
        margin: 5px 0;
        padding-left: 10px;
    }

    form textarea {
        border: 1px solid rgb(218, 218, 218);
        width: 80%;
        height: 100px;
        margin: 5px 0;
        padding: 10px 0 0 10px;
        resize: none;
    }

</style>
