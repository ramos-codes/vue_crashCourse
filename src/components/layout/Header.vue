<template>
    <header class="header-container">
        <h1 class="header-title">Todo List</h1>
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link>
        </div>
    </header>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style scoped>
    .header-container {
        margin: 10px auto;
        width: 50%;
        text-align: center;
        border-bottom: .5px solid lightgray;
    }
</style>