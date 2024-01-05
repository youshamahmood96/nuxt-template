<template>
    <div class="murmur-section">
        <textarea v-model="murmurText" placeholder="What's on your mind?" class="textarea"></textarea>
        <button @click="murmur" class="murmur-button">murmur</button>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            murmurText: ''
        };
    },
    methods: {
        murmur() {
            console.log(this.murmurText);
        },
    }
};
</script>
  
<style scoped>
.textarea {
    flex: 1;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    resize: vertical;
}

.murmur-section {
    display: flex;
    align-items: center;
    width: 100%;
    max-width: 600px;
    margin-bottom: 20px;
}

.murmur-button {
    margin-left: 10px;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    background-color: #007bff;
    color: white;
    cursor: pointer;
}
</style>
  