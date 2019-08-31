<template>
    <div id="sidebar">
        <div id="sidebar-brand" class="themed-background">
            <a href="/" class="sidebar-title">
                <span class="sidebar-nav-mini-hide"><img src="@@/assets/images/gosoft-brand.png" style="width: 50px;"></span>
            </a>
        </div>
        <div id="sidebar-scroll">
            <div class="sidebar-content">
                <sidebar-nav :nodos="nav" :ulClass="'sidebar-nav'" />
            </div>
        </div>
        <div id="sidebar-extra-info" class="sidebar-content sidebar-nav-mini-hide">
            <div class="text-center">
                <small>DashClick</small>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data: () => {
        return {
            nav: [
                {
                    name: "Cuentas",
                    to: "/cuentas",
                    icon: "fa fa-user"
                },
                {
                    name: "Reservas",
                    to: "/reservas",
                    icon: "fa fa-bed"
                }
            ]
        }
    },
    components: {
        SidebarNav: () => import(/* webpackChunkName: "SidebarNav" */ './SidebarNav')
    },
    created() {
        /*this.$store.dispatch('index', {endpoint: 'modulo'})
        .then((response) => {
            this.nav = response;
        })
        .catch(() => {
            this.$notify({
                title: 'Advertencia!',
                type: 'warning',
                content: 'Error cargando módulos',
            })
        })*/
    }
}
</script>
