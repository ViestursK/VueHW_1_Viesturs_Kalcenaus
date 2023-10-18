<template>
    <button :class="isActive ? 'active' : ''" v-on:click="setActiveTab">
        <slot></slot>
    </button>
</template>
  
<script>
export default {
    props: {
        isActive: Boolean,
    },
    methods: {
        setActiveTab() {
            this.$emit('set-active-tab');
        },
    },
};
</script>
  
<style scoped>
button {
    border: none;
    background: none;
    cursor: pointer;
    font-size: 24px;
    padding: 10px 20px;
    transition: background-color 0.3s ease, color 0.3s ease;
    color: white;
}

button:hover {
    background-color: #1e1e2e;
    color: #0056b3;
}

.active {
    background-color: purple;
    color: white;
}
</style>
  