<template>
    <header class="flex justify-between items-center p-3 bg-blue-800 min-h-10">
        <h1 class="ml-6 text-6xl text-white">Projectify</h1>
        <ul class="flex">
            <li class="mr-6" v-if="authenticated">
                <router-link :to="{name: 'dashboard'}" class="text-blue-300 hover:text-white">Dashboard</router-link>
            </li>
            <li class="mr-6" v-if="authenticated">
                <router-link :to="{name: 'projects'}" class="text-blue-300 hover:text-white">Projects</router-link>
            </li>
            <li class="mr-6" v-if="!authenticated">
                <router-link :to="{name: 'login'}" class="text-blue-300 hover:text-white">Login</router-link>
            </li>
            <li class="mr-6" v-if="authenticated">
                <a href="#" class="text-blue-300 hover:text-white" @click="handleLogout()">Logout</a>
            </li>
        </ul>
    </header>
</template>

<script>
import { mapGetters } from 'vuex';

export default {
    computed: {
        ...mapGetters([
            'authenticated'
        ])
    },
    methods: {
        async handleLogout() {
            await this.$store.dispatch('logout');
            await this.$router.push({name: 'login'});
        }
    }
}
</script>