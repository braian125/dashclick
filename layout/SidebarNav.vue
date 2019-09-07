<template>
    <ul :class="ulClass">
        <li v-for="(nodo, index) in nodos" :key="index">
            <router-link :to="nodo.children?nodo.children.length > 0?'':nodo.url:nodo.url" v-on:click.native="e => e.target.classList.toggle('open')" class="sidebar-nav-menu" :class="nodo.class">
                <span class="sidebar-nav-ripple" v-if="nodo.children?nodo.children.length > 0:false"></span>
                <i class="fa fa-chevron-left sidebar-nav-indicator sidebar-nav-mini-hide" v-if="nodo.children?nodo.children.length > 0:false"></i>
                <i class="sidebar-nav-icon" :class="nodo.icon || 'fa fa-rocket'"></i>
                <span class="sidebar-nav-mini-hide">{{ nodo.name }}</span>
            </router-link>
            <sidebar-nav v-if="nodo.children?nodo.children.length > 0:false" :nodos="nodo.children" />
        </li>
    </ul>
</template>
<script>
export default {
    name: 'sidebar-nav',
    props: {
        nodos: Array,
        ulClass: String
    },
    components: {
        SidebarNav: () => import(/* webpackChunkName: "SidebarNav" */ './SidebarNav')
    },
    methods: {
    }
}
</script>

