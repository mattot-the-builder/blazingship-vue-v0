<script setup>
    import { onMounted } from 'vue';
    import { useAuthStore } from '../stores/auth';
    import { useRouter } from 'vue-router';

    const authStore = useAuthStore();
    const router = useRouter();

    onMounted(async () => {
        await authStore.getUser();
        // router.push('/login');
    });
</script>

<template>
    <div v-if="authStore.user">
        <h1>{{ authStore.user.name }}</h1>
        <h1>{{ authStore.user.email }}</h1>
    </div>
    <div v-else>
        <h1>go and login</h1>
    </div>
</template>
