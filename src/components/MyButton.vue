<template>
    <button :style="{backgroundColor: color}" @click="btnClick" type="submit">
        <slot></slot>
    </button>
</template>

<script>
export default {
    props: {
        color:{
            default: 'black',
            type: String
        }
    },
    methods: {
        btnClick(event){
            this.$emit('clickBtn', event.target.value)
        }
    }
}
</script>

<style scoped>
button{
    width: 64px;
    height: 64px;
    border-radius: 32px;
    border: none;
    color: white;
    font-size: 24px;
}
</style>