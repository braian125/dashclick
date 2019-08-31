<template>
    <header class="navbar navbar-dark bg-dark fixed-top navbar-expand-md">
        <!-- Left Header Navigation -->
        <ul class="nav navbar-nav-custom">
            <!-- Main Sidebar Toggle Button -->
            <li class="nav-item">
                <a href="javascript:void(0)" class="nav-link" @click="sidebarToggle">
                    <i class="fa fa-ellipsis-v fa-fw animation-fadeInRight" id="sidebar-toggle-mini"></i>
                    <i class="fa fa-bars fa-fw animation-fadeInRight" id="sidebar-toggle-full"></i>
                </a>
            </li>
            <!-- END Main Sidebar Toggle Button -->
            <!-- Header Link -->
            <li class="hidden-xsd-none d-sm-block animation-fadeInQuick nav-item">
                <a href="" class="nav-link"><strong>DashClick</strong></a>
            </li>
            <!-- END Header Link -->
        </ul>
        <!-- END Left Header Navigation -->
        <!-- Right Header Navigation -->
        <ul class="nav navbar-nav-custom float-right">
            <!-- Search Form -->
            <li class="nav-item">
                <form action="page_ready_search_results.html" method="post" class="form-inline-custom">
                    <input type="text" id="top-search" name="top-search" class="form-control" placeholder="Buscar...">
                </form>
            </li>
            <!-- END Search Form -->
            <!-- Alternative Sidebar Toggle Button -->
            <li class="nav-item">
                <a href="javascript:void(0)" onclick="App.sidebar(&apos;toggle-sidebar-alt&apos;);this.blur();" class="nav-link">
                    <i class="gi gi-settings"></i>
                </a>
            </li>
            <li class="lilbell nav-item">
                <a href="javascript:void(0)" onclick="App.sidebar(&apos;toggle-sidebar-alt&apos;);this.blur();" class="nav-link">
                    <i class="gi gi-bell pulse" style="padding-top: 6px;"></i>
                </a>
            </li>
            <!-- END Alternative Sidebar Toggle Button -->
            <!-- User Dropdown -->
            <li class="dropdown nav-item"  v-bind:class="{ open: userNavItem }" v-on:click="userNavItem = !userNavItem" style="margin-right: 10px;">
                <a href="javascript:void(0)" class="dropdown-toggle nav-link" data-toggle="dropdown">
                    <img :src="user.avatar || 'https://i.pravatar.cc/150?u=bvanegas@gosoft.co'" alt="avatar">
                </a>
                <ul class="dropdown-menu dropdown-menu-right">
                    <li class="dropdown-header dropdown-item" v-if="user"> <strong>{{ user.name || 'Brian' }} {{ user.last_name || 'Vanegas' }}</strong>
                    </li>
                    <li class="dropdown-item">
                        <a href="page_app_email.html">
                            <i class="fa fa-inbox fa-fw float-right"></i>
                            Inbox
                        </a>
                    </li>
                    <li class="dropdown-item">
                        <a href="page_app_social.html">
                            <i class="fa fa-pencil-square fa-fw float-right"></i>
                            Perfil
                        </a>
                    </li>
                    <li class="dropdown-item">
                        <a href="page_app_media.html">
                            <i class="fa fa-picture-o fa-fw float-right"></i>
                            Biblioteca Multimedia
                        </a>
                    </li>
                    <li class="divider dropdown-item"></li>
                    <li class="dropdown-item"></li>
                    <li class="dropdown-item">
                        <a href="javascript:void(0)" onclick="App.sidebar(&apos;toggle-sidebar-alt&apos;);">
                            <i class="gi gi-settings fa-fw float-right"></i>
                            Ajustes
                        </a>
                    </li>
                    <li class="dropdown-item">
                        <a href="page_ready_lock_screen.html">
                            <i class="gi gi-lock fa-fw float-right"></i>
                            Bloqueo de Pantalla
                        </a>
                    </li>
                    <li class="dropdown-item">
                        <a href="" @click="logout">
                            <i class="fa fa-power-off fa-fw float-right"></i>
                            Cerrar Sesión
                        </a>
                    </li>
                </ul>
            </li>
            <!-- END User Dropdown -->
        </ul>
        <!-- END Right Header Navigation -->
    </header>
    <!-- END Header -->
</template>
<script>
export default {
    data: () => {
        return {
            userNavItem: false
        }
    },
    computed: {
        user() {
            return {}
        }
    },
    methods: {
        sidebarToggle () {
            this.$emit('sidebarToggle')
        },
        logout() {
            //this.$store.dispatch('user/logout')
        }
    }
}
</script>