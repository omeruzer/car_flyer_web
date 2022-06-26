<template>
    <div>
        <div class="content">
            <div class="container">
                <div class="row mt-3">
                    <div class="col-md-12">
                        <div class="row">
                            <div class="col-md-3 mb-3" v-for="item, i in cars.cars" :key="i">
                                <ProductCard :item="item" />
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            cars: {}
        }
    },
    created() {
        this.getCars()
    },
    methods: {
        async getCars() {
            await this.$axios.get(`http://localhost:5000/api/model/${this.$route.params.id}`)
                .then((result) => {
                    this.cars = result.data
                    console.log(result.data);
                }).catch((err) => {

                });
        }
    }
}
</script>

<style lang="scss" scoped>
</style>