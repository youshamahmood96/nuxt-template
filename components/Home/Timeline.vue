<template>
    <div class="timeline">
        <div v-for="murmur in murmurs" :key="murmur.id" class="murmur">
            <div class="murmur-header">
                <!--  use userID instead of murmur.id -->
                <NuxtLink :to="`/user/${murmur.userId}`" class="username-link">{{ murmur.username }}</NuxtLink>
                <span class="murmur-date">{{ murmur.date }}</span>
            </div>
            <div class="murmur-content">
                {{ murmur.content }}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            murmurs: []
        };
    },
    mounted() {
        this.fetchMurmurs();
    },
    methods: {
        async fetchMurmurs() {
            try {
                const response = await this.$axios.$get('https://jsonplaceholder.typicode.com/posts');
                this.murmurs = response.map(item => ({
                    id: item.id,
                    userId: item.userId,
                    username: 'User' + item.userId,  // For simplicity, appending 'User' to user ID
                    date: new Date().toISOString().slice(0, 10), // Using today's date for simplicity
                    content: item.title // Assuming the title as the content for this example
                }));
            } catch (error) {
                console.error('Error fetching data:', error);
            }
        }

    }
};
</script>


<style scoped>
.murmur {
    background-color: #ffffff;
    border: 1px solid #e0e0e0;
    border-radius: 10px;
    padding: 15px;
    margin-bottom: 20px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.murmur-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;
}

.username-link {
    font-weight: bold;
    color: #1877F2;
    text-decoration: none;
    cursor: pointer;
    transition: color 0.3s ease;
}

.username-link:hover {
    color: #1155cc;
}

.murmur-date {
    font-size: 14px;
    color: #777777;
}

.murmur-content {
    font-size: 16px;
    line-height: 1.5;
    color: #333333;
}

.timeline {
    width: 100%;
    max-width: 600px;
}

.murmur {
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
}
</style>