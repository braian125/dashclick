<template>
    <div id="actions-bar" class="row p-0 m-0 mb-3 w-100">
        <div class="col">
            <breadcrumb />
        </div>
        <div class="col">
            <ul>
                <li v-for="(action, index) in actions" class="d-inline p-2">
                    <router-link :to="action.url" :key="index">
                        <font-awesome-icon :icon="action.icon || 'rocket'"></font-awesome-icon>
                    </router-link>
                </li>
            </ul>
        </div>
    </div>
</template>
<script>
export default {
    name: 'ActionBar',
    props: {
      actions: {
        type: Array,
        required: true,
        default: () => []
      }
    },
    components: {
        Breadcrumb: () => import(/* webpackChunkName: "breadcrumb" */ '@@/layout/Breadcrumb'),
    }
}
</script>