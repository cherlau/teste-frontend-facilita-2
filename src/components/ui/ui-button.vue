<template>
        <button
            :type="type"
            :disabled="disabled"
            :class="[design, 'ui-button', { 'disabled': disabled }]"
            @click="callback($event)"
        >
            <i v-if="leftIcon" :class="leftIcon"></i>

            <template v-if="!loading">
                <slot></slot>
            </template>

            <svg v-if="loading" class="loading" width="27" height="28" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" fill="#ffffff"><path d="M12,1A11,11,0,1,0,23,12,11,11,0,0,0,12,1Zm0,19a8,8,0,1,1,8-8A8,8,0,0,1,12,20Z" opacity=".25"/><path d="M10.14,1.16a11,11,0,0,0-9,8.92A1.59,1.59,0,0,0,2.46,12,1.52,1.52,0,0,0,4.11,10.7a8,8,0,0,1,6.66-6.61A1.42,1.42,0,0,0,12,2.69h0A1.57,1.57,0,0,0,10.14,1.16Z"><animateTransform attributeName="transform" type="rotate" dur="0.75s" values="0 12 12;360 12 12" repeatCount="indefinite"/></path></svg>
        </button>
</template>

<script>

export default {
    name: 'ui-button',
    props: {
        type:{
            type: String,
            required: false,
            default: 'button'
        },
        loading: {
            type: Boolean,
            required: false,
            default: false
        },
        disabled: {
			type: Boolean,
			required: false,
			default: false
		},
        leftIcon:{
            type: String,
            required: false,
            default: ''
        },
        design:{
            type: String,
            required: false,
            default: ''
        },
        background: {
            type: String,
            required: false,
            default: 'transparent'
        },
        color: {
            type: String,
            required: false,
            default: ''
        },
    },
    methods: {
		callback: function(e) {
            if(this.type === 'submit'){
                this.$emit('update:submit', e);
            }else{
                this.$emit('click-button', e);
            }
			
		}
	},
}

</script>

<style lang="stylus" scoped>
    @import '../../assets/stylus/styles.styl';
</style> 
