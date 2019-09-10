<template>
    <div id="sidebar-alt" tabindex="-1" aria-hidden="true">
        <!-- Toggle Alternative Sidebar Button (visible only in static layout)
        --> <a href="javascript:void(0)" id="sidebar-alt-close" onclick="App.sidebar(&apos;toggle-sidebar-alt&apos;);"><i class="fa fa-times"></i></a>
        <!--
        Wrapper for scrolling functionality -->
        <div id="sidebar-scroll-alt">
            <!-- Sidebar Content -->
            <div class="sidebar-content">
                <!-- Profile -->
                <div class="sidebar-section">
                    <h2 class="text-dark">Perfil</h2>
                </div>
                <!-- END Profile -->
                <!-- Settings -->
                <div class="sidebar-section">
                    <h2 class="text-dark">Ajustes</h2>
                </div>
                <!-- END Settings -->
            </div>
            <!-- END Sidebar Content -->
        </div>
        <!-- END Wrapper for scrolling functionality -->
    </div>
</template>
<script>
export default {

}
</script>