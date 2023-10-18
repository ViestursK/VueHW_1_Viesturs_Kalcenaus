<template>
    <header class="header" :style="{ backgroundColor: headerBackgroundColor }">
        <img src="@/assets/logo.svg" alt="Logo" class="logo" />
        <div class="right">
            <div class="user-info" v-if="isLoggedIn">
                <div class="avatar" :style="{ backgroundColor: getRandomColor() }">
                    <span class="user-initials">{{ user.name.charAt(0) }}{{ user.surname.charAt(0) }}</span>
                </div>
                <span class="user-name">{{ full_name }}</span>
            </div>
            <button @click="toggleLoginStatus">{{ isLoggedIn ? 'LOGOUT' : 'LOGIN' }}</button>
        </div>
    </header>
</template>
  
<script>
export default {
    data() {
        return {
            isLoggedIn: false,
            headerBackgroundColor: '',
            user: {
                name: "Viesturs",
                surname: "Kalcenaus",
                code: "IT21021"
            }
        };
    },
    computed: {
        full_name() {
            return `${this.user.name} ${this.user.surname}`;
        }
    },
    methods: {
        toggleLoginStatus() {
            if (this.isLoggedIn) {
                if (window.confirm('Do you want to log out?')) {
                    this.logout();
                }
            } else {
                if (window.confirm('Do you want to log in?')) {
                    this.login();
                }
            }
        },
        login() {
            this.isLoggedIn = true;
            this.avatarColor = '';
            this.headerBackgroundColor = '#007bff';
            this.$emit('login', true);
        },
        logout() {
            this.isLoggedIn = false;
            this.headerBackgroundColor = '';
            this.avatarColor = '';
            this.$emit('login', false);
        },
        getRandomColor() {
            const letters = '0123456789ABCDEF';
            let color = '#';
            for (let i = 0; i < 6; i++) {
                color += letters[Math.round(Math.random() * 15)];
            }
            return color;
        }
    }
};
</script>
  
<style scoped>
.header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 99;
    display: flex;
    justify-content: space-between;
    background-color: darkslateblue;
}

.user-initials {
    font-size: 24px;
    font-weight: bold;
}

.user-name {
    margin-right: 20px;
}

.logo {
    width: 50px;
    height: 50px;
    filter: invert(100%);
    margin: 10px;
}

.user-info {
    display: flex;
    align-items: center;
    border-right: 2px solid #f0f0f0;
}

.right {
    display: flex;
    align-items: center;
}

.avatar {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-right: 10px;
    color: white;
}

.user-name {
    font-weight: bold;
    color: #f0f0f0;
}

button {
    background-color: purple;
    color: white;
    border: none;
    padding: 10px 20px;
    border-radius: 50px;
    cursor: pointer;
    transition: background-color 0.3s ease;
    margin: 10px;
}

button:hover {
    background-color: darkslateblue;
}
</style>
  