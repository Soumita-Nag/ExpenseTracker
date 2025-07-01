<template>
    <div class="flex flex-wrap justify-between p-4 bg-[var(--color-bg-secondary-dark)]">
        <h2>Expense Tracker</h2>
        <button v-if="theme=='dark'" type="button">☀️</button>
        <button v-else-if="theme=='light'" type="button">🌙</button>

    </div>
</template>
<script>
    export default{
        data(){
            return{
                
            }
        },
        props:{
            theme:String,
        },
        methods:{
            
        },
    }
</script>
<style scoped>
    
</style>