<template>
    <b-navbar class="header">
        <b-navbar class="container">
            <nuxt-link to="/" tag="a" class="navbar-brand text-white">ArabaSat</nuxt-link>
            <b-navbar-nav>
                <b-nav-item href="#">
                    <nuxt-link to="/new-car"><b-button variant="warning text-white">Ücretsiz İlan Ver</b-button></nuxt-link>
                </b-nav-item>
            </b-navbar-nav>
        </b-navbar>
    </b-navbar>
</template>

<script>
export default {

}
</script>

<style scoped>
.header {
    background-color: #992726;
}
</style>