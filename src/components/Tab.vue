<template>
    <li v-for="tab in tabs" :key="tab" @click="changeTab(tab)" :pushed="false" :class="[`tab`, {active:currentTab === tab}]">
        <a>
            {{tab}}
        </a>
    </li>
</template>

<script>

    export default {
        name: 'Button',
        emits: ['tabChange'],
        data() {
            return {
                currentTab: 'Stored Resource',
                tabs: ['Stored Resource', 'Add Resource'],
                isSwitched: true,
                pushed: this.isPushed
            }
        },
        methods: {
            changeTab(tab) {
                this.currentTab = tab
                if (tab === 'Stored Resource') {
                    this.isSwitched = true
                } else {
                    this.isSwitched = false
                }

                this.$parent.$emit('tabChange', this.isSwitched)
            },
            backtoHome(tab) {
                this.currentTab = tab
            }
        },
        props: ['a-text']
    }
</script>

<style scoped>
    .tab {
        width: 200px;
        min-height: 50px;
        background-color: #FFF;
        border-radius: 4px;
        display: flex;
        align-items: center;
        transition: all 0.3s;
        font-size: 15px;
        margin-left: 20px;
    }

    .tab a {
        width: 100%;
        height: 100%;
        text-decoration: none;
        color: rgb(71, 22, 110);
        display: flex;
        justify-content: center;
    }

    .tab:hover {
        background-color: rgb(236, 224, 245);
        transition: all 0.3s;
        cursor: pointer;
    }

    .active {
        background-color: rgb(71, 22, 110);
    }

    .active:hover {
        background-color: rgb(71, 22, 110);
        transition: all 0.3s;
        cursor: pointer;
    }

    .active a {
        color: #FFF;
    }

</style>
