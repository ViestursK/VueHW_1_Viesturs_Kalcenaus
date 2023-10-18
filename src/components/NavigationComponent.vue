<!-- NavigationComponent.vue -->
<template>
    <div class="nav">
        <NavigationButton v-if="isLoggedIn" :isActive="activeTab === 'home'" @set-active-tab="setActiveTab('home')">HOME
        </NavigationButton>
        <NavigationButton v-if="isLoggedIn" :isActive="activeTab === 'about'" @set-active-tab="setActiveTab('about')">ABOUT
            ME</NavigationButton>
    </div>
</template>
  
<script>
import NavigationButton from './NavigationButton.vue';
import HomeComponent from './HomeComponent.vue';
import AboutMeComponent from './AboutMeComponent.vue';

export default {
    components: {
        NavigationButton,
    },
    data() {
        return {
            activeTab: 'home',
        };
    },
    props: ['activeTab', 'isLoggedIn'],
    methods: {
        setActiveTab(tab) {
            this.activeTab = tab;
            this.$emit('change-tab', tab == 'home' ? HomeComponent : AboutMeComponent);
        },
    },
};
</script>
<style scoped>
.nav {
    display: flex;
    flex-direction: column;
    align-items: start;
    justify-content: flex-start;
    height: 100%;
    border-right: 2px #007BFF solid;
    margin-right: 30px;
    width: 300px;
}
</style>
  