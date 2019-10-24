<template>
    <div id="actions-bar" class="w-100">
        <ul>
            <li v-for="(action, index) in actions" class="d-inline p-2">
                <router-link :to="action.url" :key="index">
                    <font-awesome-icon :icon="action.icon || 'rocket'"></font-awesome-icon>
                </router-link>
            </li>
        </ul>
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
    }
}
</script>