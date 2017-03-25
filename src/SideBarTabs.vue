<template>
    <div>
        <aside class="background-is-black-transparent side-navigation right">
            <div class="tabs is-centered margin-bottom-none background-is-black-transparent">
                <ul id="tab-top-menu">
                    <li v-for="tab in tabs" :class="{ 'is-active':tab.isActive }">
                        <a :href="tab.href" @click="selectTab(tab)">
                            <i class="fa fa-fw" v-bind:class="tab.icon" aria-hidden="true"></i>
                        </a>
                    </li>
                </ul>
                <a class="close-side-bar-button color-is-danger" v-on:click="toogleSideBarMenu"><i class="fa fa-fw fa-close" aria-hidden="true"></i></a>
            </div>
            <div class="tab-content">
                <slot></slot>
            </div>
        </aside>
    </div>
</template>
<script>
'use strict';
export default {
    data () {
        return {
            tabs: []
        };
    },
    created () {
        this.tabs = this.$children;
    },
    methods: {
        selectTab (selectedTab) {
            this.tabs.forEach(tab => {
                if(tab.name === selectedTab.name) {
                    tab.isActive = true;
                }
                else {
                    tab.isActive = false;
                }
            });
        },
        toogleSideBarMenu () {
            this.$emit('toogleSideBarMenu');
        }
    }
};
</script>
