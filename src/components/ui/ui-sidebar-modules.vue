<template>
    <div class="sidebar-module-item" :class="{ 'highlighted': isHighlighted }" @click="toggleCategories">
        <span v-html="module.icon"></span>
        <h3>{{ module.name }}</h3>
    </div>
</template>

<script>
export default {
    name: 'UiSidebarModules',
    props: {
        module: Object,
        moduleName: String,
        isHighlighted: Boolean,
    },
    methods: {
        toggleCategories() {
            this.$emit('clickChangeView', this.module.categories, this.moduleName)
            this.$emit('clickChangeHighlight', this.moduleName);
        }
    },
}
</script>

<style lang="stylus" scoped>
    @import '../../assets/stylus/styles.styl';

    &div:last-of-type 
        border-bottom: 1px solid rgba(255, 255, 255, 0.219)
</style> 

