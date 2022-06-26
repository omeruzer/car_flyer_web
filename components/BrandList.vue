<template>
    <b-list-group>
        <b-list-group-item v-for="item,i in categories.brands" :key="i">
            <nuxt-link :to="{name:'brand-id',params:{id:item._id}}" class="list-item"> {{item.name}}</nuxt-link>
        </b-list-group-item>
    </b-list-group>
</template>

<script>
export default {
    data() {
        return {
            categories:{}
        }
    },
    created(){
        this.getCategories()
    },
    methods:{
        async getCategories(){
            await this.$axios.get(`http://localhost:5000/api/category/${this.$route.params.id}`)
                .then((result) => {
                    this.categories=result.data
                }).catch((err) => {
                    
                });
        }
    }
}
</script>

<style scoped>

.list-item{
    display: flex;
    

}
.icon{
width: 30px;
margin-right: 20px;
}
</style>