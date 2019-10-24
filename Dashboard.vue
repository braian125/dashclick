<template>
    <div id="page-wrapper">
        <div id="page-container" class="header-fixed-top sidebar-d-none d-lg-block d-xl-none-full" v-bind:class="{ 'sidebar-visible-lg-full' : sidebarFull, 'sidebar-visible-lg-mini' : sidebarMini }">
            <sidebar-alt/>
            <sidebar/>
            <div id="main-container">
                <header-app @sidebarToggle="sidebarToggle" @logout="logout" />
                <div id="page-content">
                    <action-bar :actions="childrenNavs.children" />
                    <breadcrumb :breadcrumb="breadcrumb"/>
                    <router-view/>
                </div>
            </div>
        </div>
    </div>
</template>
<script>

export default {
    name: 'Dashclick',
    data: () => {
        return {
            sidebarFull: true,
            sidebarMini: false
        }
    },
    computed: {
        breadcrumb() {
            return this.$route.matched.filter(
                route => route.name || route.meta.label
            );
        },
        childrenNavs() {
            return this.$store.getters['layout/sidebarNav'].find(nav => nav.url == this.$route.path) || []
        }
    },
    components: {
        SidebarAlt: () => import(/* webpackChunkName: "sidebarAlt" */ '@@/layout/SidebarAlt'),
        Sidebar: () => import(/* webpackChunkName: "sidebar" */ '@@/layout/Sidebar'),
        HeaderApp: () => import(/* webpackChunkName: "header" */ '@@/layout/Header'),
        Breadcrumb: () => import(/* webpackChunkName: "breadcrumb" */ '@@/layout/Breadcrumb'),
        ActionBar: () => import(/* webpackChunkName: "actionBar" */ '@@/layout/ActionBar')
    },
    methods: {
        sidebarToggle() {
          this.sidebarFull = !this.sidebarFull;
          this.sidebarMini = !this.sidebarMini;
        },
        logout() {

        }
    }
}
</script>
