<template>
    <div>
        <element-list v-for="(data, index) in listData" @deleteEvent="deletePost(index)" :key="index" :data="data"></element-list>
    </div>
</template>

<script>
    import ElementList from './ElementList.vue'
    export default {
        name: 'show-list-assets',
        components: {
            ElementList
        },
        props: {
            listData: {
                type: Array
            }
        },
        data() {
            return {
                ListElements: this.listData
            }
        },
        methods: {
            deletePost(index) {
                this.ListElements.splice(index, 1)
            }
        }
    }
</script>

<style scoped></style>
