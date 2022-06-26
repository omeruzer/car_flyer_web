<template>
    <div>
        <nuxt-link :to="{ name: 'car-id', params: { id: item._id } }">
            <div class="card">
                <div class="image">
                    <img :src="item.images[0]" alt="" srcset="">
                </div>
                <div class="info">
                    <div class="text-area">
                        <div class="brand">{{ item.brand.name }}</div>
                        <div class="car-info">{{ item.model.name }} - {{ item.year.year }} - {{ item.km }} km</div>
                    </div>
                    <div class="city">{{ item.city.city }}</div>
                </div>
                <div class="price">{{ item.price }} ₺</div>
            </div>
        </nuxt-link>
    </div>
</template>

<script>
export default {
    props: ['item']
}
</script>

<style  scoped>
.image img {
    width: 100%;
    border-radius: 3%;
}

.brand {
    font-weight: bold;
    color: #992726;

}

a {
    text-decoration: none;
}

.car-info {
    color: gray;
}

.city {
    color: #992726;
}

.card {
    border-radius: 3%;
}

.price {
    padding: 5px;
    display: flex;
    justify-content: end;
    color: #992726;
    font-weight: bold;
    font-size: 18px;
}

.info {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 5px;
}
</style>