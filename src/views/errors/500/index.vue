<script lang="ts" setup>
import { useRouter } from 'vue-router'

const router = useRouter()

function goHome() {
    router.push('/')
}
</script>
<template>
    <div class="flex h-full">
        <el-button type="primary" @click="goHome">Go To Home</el-button>
    </div>
</template>