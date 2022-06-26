<template>
    <div>
        <div v-if="loading" class="container mt-4">
            <div class="row mb-4">
                <div class="car-name">{{ car.name }}</div>
            </div>
            <div class="row">
                <div class="col-md-6">
                    <div>
                        <b-carousel id="carousel-1" v-model="slide" :interval="4000" controls indicators
                            background="#ababab" img-width="1024" img-height="480"
                            style="text-shadow: 1px 1px 2px #333;" @sliding-start="onSlideStart"
                            @sliding-end="onSlideEnd">
                            <b-carousel-slide v-for="item, i in car.images" :key="i" :img-src="item"></b-carousel-slide>
                        </b-carousel>
                    </div>
                </div>
                <div class="col-md-3">
                    <div class="row">
                        <div class="d-flex w-100 justify-content-end">
                            <h4 class="price">{{ car.price }} ₺</h4>
                        </div>
                    </div>
                    <div class="row">
                        <h6>{{ car.city.city }} / {{ car.district.district }} / {{ car.street.street }}</h6>
                    </div>
                    <div class="row">
                        <div class="d-flex w-100 justify-content-between px-4 one">
                            <div class="feature">İlan NO</div>
                            <div class="value">11</div>
                        </div>
                    </div>
                    <!-- <div class="row">
                        <div class="d-flex w-100 justify-content-between px-4 two">
                            <div class="feature">İlan Tarihi</div>
                            <div class="value">{{  car.date }}</div>
                        </div>
                    </div> -->
                    <div class="row">
                        <div class="d-flex w-100 justify-content-between px-4 one">
                            <div class="feature">Marka</div>
                            <div class="value">{{ car.brand.name }}</div>
                        </div>
                    </div>
                    <div class="row">
                        <div class="d-flex w-100 justify-content-between px-4 two">
                            <div class="feature">Model</div>
                            <div class="value">{{ car.model.name }}</div>
                        </div>
                    </div>
                    <div class="row">
                        <div class="d-flex w-100 justify-content-between px-4 one">
                            <div class="feature">Yıl</div>
                            <div class="value">{{ car.year.year }}</div>
                        </div>
                    </div>
                    <div class="row">
                        <div class="d-flex w-100 justify-content-between px-4 two">
                            <div class="feature">Kilometre</div>
                            <div class="value">{{ car.km }} km</div>
                        </div>
                    </div>
                    <div class="row">
                        <div class="d-flex w-100 justify-content-between px-4 one">
                            <div class="feature">Vites Tipi</div>
                            <div class="value">{{ car.gear.name }}</div>
                        </div>
                    </div>
                    <div class="row">
                        <div class="d-flex w-100 justify-content-between px-4 two">
                            <div class="feature">Yakıt Tipi</div>
                            <div class="value">{{ car.fuel.name }}</div>
                        </div>
                    </div>
                    <div class="row">
                        <div class="d-flex w-100 justify-content-between px-4 one">
                            <div class="feature">Kasa Tipi</div>
                            <div class="value">{{ car.case.name }}</div>
                        </div>
                    </div>
                    <div class="row">
                        <div class="d-flex w-100 justify-content-between px-4 two">
                            <div class="feature">Motor Hacmi</div>
                            <div class="value">{{ car.engine_capacity }}</div>
                        </div>
                    </div>
                    <div class="row">
                        <div class="d-flex w-100 justify-content-between px-4 one">
                            <div class="feature">Motor Gücü</div>
                            <div class="value">{{ car.engine_power }}</div>
                        </div>
                    </div>
                    <div class="row">
                        <div class="d-flex w-100 justify-content-between px-4 two">
                            <div class="feature">Çekiş</div>
                            <div class="value">{{ car.traction.name }}</div>
                        </div>
                    </div>
                    <div class="row">
                        <div class="d-flex w-100 justify-content-between px-4 one">
                            <div class="feature">Ort. Yakıt Tüketi</div>
                            <div class="value">{{ car.fuel_cons }}</div>
                        </div>
                    </div>
                    <div class="row">
                        <div class="d-flex w-100 justify-content-between px-4 two">
                            <div class="feature">Yakıt Deposu</div>
                            <div class="value">{{ car.fuel_tank }}</div>
                        </div>
                    </div>
                    <div class="row">
                        <div class="d-flex w-100 justify-content-between px-4 one">
                            <div class="feature">Kimden</div>
                            <div class="value">{{ car.fromWho.name }}</div>
                        </div>
                    </div>
                </div>
                <div class="col-md-3">
                    <div class="card">
                        <div class="d-column ">
                            <div class="row">
                                <div class="col-md-12">
                                    <h5 class="text-center">İletişim Bilgileri</h5>
                                </div>
                            </div>
                            <div class="d-flex justify-content-center">
                                <span>{{ car.contact_name }}</span>
                            </div>
                            <div class="d-flex justify-content-center">
                                <span style="font-weight: bold;">{{ car.contact_phone }}</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div v-else class="d-flex justify-content-center" style="margin-top: 150px;">
            <b-spinner label="Spinning"></b-spinner>

        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            car: {},
            loading: false
        }
    },
    created() {
        this.getCar()
    },
    methods: {
        async getCar() {
            await this.$axios.get(`http://localhost:5000/api/car/${this.$route.params.id}`)
                .then((result) => {
                    this.car = result.data
                    this.loading = true
                }).catch((err) => {

                });
        }
    }
}
</script>

<style scoped>
.one {
    background-color: #d6d6d6;
}

.two {
    background-color: #fff;
}

.price {
    color: #992726;
    font-weight: bold;

}

.car-name {
    font-weight: bold;
    font-size: 18px;
    
}
</style>