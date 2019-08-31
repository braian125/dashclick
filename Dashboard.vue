<template>
    <div id="page-wrapper">
        <div id="page-container" class="header-fixed-top sidebar-d-none d-lg-block d-xl-none-full" v-bind:class="{ 'sidebar-visible-lg-full' : sidebarFull, 'sidebar-visible-lg-mini' : sidebarMini }">
        <!--alternative-sidebar/-->
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
/*import AlternativeSidebar from '@@/layout/AlternativeSidebar'
import Sidebar from '@@/layout/Sidebar'
import HeaderApp from '@@/layout/Header'*/

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
        //AlternativeSidebar,
        Sidebar: () => import('@@/dashclick/layout/Sidebar'),
        HeaderApp: () => import('@@/dashclick/layout/Header'),
        /*Breadcrumb: () => import('@@/layout/Breadcrumb')*/
    }
}
</script>
