<template>
    <b-list-group>
        <b-list-group-item v-for="item,i in categories" :key="i">
            <nuxt-link :to="{name:'category-id',params:{id:item._id}}" class="list-item"> {{item.name}}</nuxt-link>
        </b-list-group-item>
    </b-list-group>
</template>

<script>
export default {
    data() {
        return {
            categories:[]
        }
    },
    created(){
        this.getCategories()
    },
    methods:{
        async getCategories(){
            await this.$axios.get('http://localhost:5000/api/category')
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
    color: #992726;
}
a{
    text-decoration: none;
}

.icon{
width: 30px;
margin-right: 20px;
}
</style>