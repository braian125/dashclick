<template>
    <div id="page-wrapper">
        <div id="page-container" class="header-fixed-top sidebar-d-none d-lg-block d-xl-none-full" v-bind:class="{ 'sidebar-visible-lg-full' : sidebarFull, 'sidebar-visible-lg-mini' : sidebarMini }">
        <sidebar-alt/>
        <sidebar/>
        <div id="main-container">
            <header-app @sidebarToggle="sidebarToggle" />
            <div id="page-content">
                <!--breadcrumb/-->
                <router-view/>
            </div>
        </div>
        </div>
    </div>
</template>
<script>

export default {
    data: () => {
        return {
            sidebarFull: true,
            sidebarMini: false
        }
    },
    methods: {
        sidebarToggle() {
            this.sidebarFull = !this.sidebarFull;
            this.sidebarMini = !this.sidebarMini;
        }
    },
    components: {
        SidebarAlt: () => import(/* webpackChunkName: "sidebarAlt" */ '@@/dashclick/layout/SidebarAlt'),
        Sidebar: () => import(/* webpackChunkName: "sidebar" */ '@@/layout/Sidebar'),
        HeaderApp: () => import(/* webpackChunkName: "header" */ '@@/layout/Header'),
        /*Breadcrumb: () => import('@@/layout/Breadcrumb')*/
    }
}
</script>
