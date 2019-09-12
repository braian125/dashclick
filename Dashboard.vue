<template>
    <div id="page-wrapper">
        <div id="page-container" class="header-fixed-top sidebar-d-none d-lg-block d-xl-none-full" v-bind:class="{ 'sidebar-visible-lg-full' : sidebarFull, 'sidebar-visible-lg-mini' : sidebarMini }">
        <!--alternative-sidebar/-->
        <sidebar/>
        <div id="main-container">
            <header-app @sidebarToggle="sidebarToggle" @logout="logout" />
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
    props: {
      user: {
          type: Object,
          required: false,
          default: () => {}
      },
      getSidebarNav: {
          type: Boolean,
          required: false,
          default: () => false
      }
    },
    methods: {
        sidebarToggle() {
            this.sidebarFull = !this.sidebarFull;
            this.sidebarMini = !this.sidebarMini;
        },
        logout() {
            this.$emit('logout')
        }
    },
    components: {
        //AlternativeSidebar,
        Sidebar: () => import('@@/layout/Sidebar'),
        HeaderApp: () => import('@@/layout/Header'),
        /*Breadcrumb: () => import('@@/layout/Breadcrumb')*/
    },
    created() {
      if (this.getSidebarNav) {
        this.$store.dispatch('fetch', {endpoint: 'admin/component'})
        .then((response) => {
          this.$store.commit('SET_SIDEBARN_NAV', response)
        })
        .catch(() => {
          this.$notify({
            title: 'Advertencia!',
            type: 'warning',
            content: 'Error cargando módulos',
          })
        })
      }
    }
}
</script>
