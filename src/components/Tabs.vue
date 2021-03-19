<template>
    <header>
        <nav>
            <ul>
                <tab></tab>
            </ul>
        </nav>
    </header>
</template>

<script>
    import Tab from './Tab.vue'
    export default {
        name: 'tabs',
        data() {
            return {
            }
        },
        components: {
            Tab
        }
    }
</script>

<style scoped>
    header {
        width: 100%;
        background-color: #FFF;
        height: 90px;
    }

    header nav {
        height: 100%;
        width: 100%;
    }

    header nav ul {
        width: 100%;
        display: flex;
        align-items: center;
        height: 100%;
    }

    header nav ul li {
        width: 200px;
        height: 40px;
        margin-left: 20px;
    }

</style>
