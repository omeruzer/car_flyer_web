<template>
    <b-list-group>
        <b-list-group-item v-for="item, i in brand.models" :key="i">
            <nuxt-link :to="{ name: 'model-id', params: { id: item._id } }" class="list-item"> {{ item.name }}
            </nuxt-link>
        </b-list-group-item>
    </b-list-group>
</template>

<script>
export default {
    data() {
        return {
            brand: {}
        }
    },
    created() {
        this.getbrand()
    },
    methods: {
        async getbrand() {
            await this.$axios.get(`http://localhost:5000/api/brand/${this.$route.params.id}`)
                .then((result) => {
                    this.brand = result.data
                }).catch((err) => {

                });
        }
    }
}
</script>

<style lang="scss" scoped>
</style>