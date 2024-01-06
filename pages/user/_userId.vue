<template>
    <div class="user-container">
        <h1>User Profile</h1>
        <div class="user-details">
            <div class="detail">
                <label>Name:</label>
                <p>{{ user.name }}</p>
            </div>
            <div class="detail">
                <label>Email:</label>
                <p>{{ user.email }}</p>
            </div>
            <div class="detail">
                <label>Phone:</label>
                <p>{{ user.phone }}</p>
            </div>
        </div>
    </div>
</template>
  
<script lang="ts">
import { NuxtAxiosInstance } from '@nuxtjs/axios';
export default {
    async asyncData({ params, $axios }: { params: { userId: string }, $axios: NuxtAxiosInstance }) {
        try {
            const response = await $axios.$get(`https://jsonplaceholder.typicode.com/users/${params.userId}`);
            return { user: response };
        } catch (error) {
            console.error('Error fetching user:', error);
        }
    },
}
</script>
  
<style scoped>
.user-container {
    max-width: 600px;
    margin: 50px auto;
    padding: 20px;
    border-radius: 8px;
    background-color: #f7f7f7;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    font-family: Arial, sans-serif;
}

.user-container h1 {
    text-align: center;
    margin-bottom: 20px;
}

.user-details {
    background-color: #ffffff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.detail {
    display: flex;
    justify-content: space-between;
    margin-bottom: 15px;
}

.detail label {
    font-weight: bold;
}

.detail p {
    margin-left: 10px;
    color: #333333;
}
</style>
  