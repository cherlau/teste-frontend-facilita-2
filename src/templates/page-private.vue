<template>
    <div class="task-page">
        <ui-sidebar class="side-bar" @modulesClick="handleClick"></ui-sidebar>
        <div class="task-page-content">
            <ui-header></ui-header>
            <component :is="moduleSelected"></component>
        </div>
    </div>
</template>

<script>
import UiSidebar from "@/components/ui/ui-sidebar";
import UiHeader from "@/components/ui/ui-header";
import ViewDashboard from "@/views/view-dashboard";
import ViewTasks from "@/views/view-tasks"
import ViewSettings from "@/views/view-settings";
import { ref, computed } from "vue";

export default {
    name: "PagePrivate",
    components: {
        UiSidebar,
        UiHeader,
        ViewDashboard,
        ViewTasks,
        ViewSettings
    },
    setup() {
        const moduleKey = ref("dashboard");

        function handleClick(key) {
            moduleKey.value = key;
        }

        const moduleSelected = computed(() => {
            switch (moduleKey.value) {
                case "dashboard": return ViewDashboard;
                case "tasks":     return ViewTasks;
                case "settings":  return ViewSettings;
                default:          return ViewDashboard;
            }
        });

        return { handleClick, moduleSelected };
    },
};
</script>

<style lang="stylus" scoped>
  @import '../assets/stylus/styles.styl'; 
</style>