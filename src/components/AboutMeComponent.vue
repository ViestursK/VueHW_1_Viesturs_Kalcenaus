<template>
    <div>
        <h1>ABOUT ME</h1>
        <h3>Name: {{ user.name }}</h3>
        <h3>Surname: {{ user.surname }}</h3>
        <h3>Code: {{ user.code }}</h3>
    </div>
</template>
  
<script>
export default {
    name: 'AboutMeComponent',
    data() {
        return {
            user: {
                name: 'Viesturs',
                surname: 'Kalcenaus',
                code: 'IT21021'
            }
        };
    }
};
</script>
<style scoped>
h1 {
    font-size: 48px;
    color: #f0f0f0;
}

h3 {
    font-size: 24px;
    color: #a0a0a0;
    margin-top: 20px;
}
</style>