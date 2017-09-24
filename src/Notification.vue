<template>
    <div class="notification" :class="type" v-show="! isHidden">
        <button class="delete" @click="close" v-if="isCloseable"></button>
        <slot></slot>
    </div>
</template>

<script>
    export default {
        computed: {
            isHidden() {
                return this.getState()
            }
        },

        data() {
            return {
                isHiddenLocalState: false,
            }
        },

        methods: {
            close() {
                if (this.remember) {
                    localStorage.setItem('vue-bulma-notifications', JSON.stringify(true))
                }                

                return this.isHiddenLocalState = true
            },

            getState() {
                const savedState = localStorage.getItem('vue-bulma-notifications')

                return (savedState && this.remember) ? JSON.parse(savedState) : this.isHiddenLocalState
            }
        },

        mounted() {
            if (this.autoCloseAfter > 0) {
                setTimeout(() => {
                    this.isHidden = true;
                }, this.autoCloseAfter)
            }
        },

        props: {
            autoCloseAfter: {
                default: 0,
                type: Number,
            },

            isCloseable: {
                default: true,
                type: Boolean,
            },

            remember: {
                default: false,
                type: Boolean,
            },

            type: {
                type: String,
                default: ''
            }
        },
    }
</script>
