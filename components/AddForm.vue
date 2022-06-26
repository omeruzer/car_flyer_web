<template>
    <div>
        <h5>Araba İlanı Ekle</h5>
        <hr>
        <div class="row">
            <div class="col-md-6">
                <b-form-group>
                    <label for="">İlan Resimleri</label>
                    <b-form-file id="input-horizontal"></b-form-file>
                </b-form-group>
                <b-form-group>
                    <label for="">İlan Adı</label>
                    <b-form-input v-model="form.name" id="input-horizontal"></b-form-input>
                </b-form-group>
                <b-form-group>
                    <label for="">Kategori</label>
                    <select class="form-control" v-model="form.category" @change="getBrand" name="" id="">
                        <option v-for="item, i in categories" :key="i" :value="item._id">{{ item.name }}</option>
                    </select>
                </b-form-group>
                <b-form-group v-if="isVisibiltyBrands">
                    <label for="">Marka</label>
                    <select class="form-control" v-model="form.brand" @change="getModel" name="" id="">
                        <option v-for="item, i in brands.brands" :key="i" :value="item._id">{{ item.name }}</option>
                    </select>
                </b-form-group>
                <b-form-group v-if="isVisibiltyModels">
                    <label for="">Model</label>
                    <select class="form-control" v-model="form.model" name="" id="">
                        <option v-for="item, i in models.models" :key="i" :value="item._id">{{ item.name }}</option>
                    </select>
                </b-form-group>
                <b-form-group>
                    <label for="">Yıl</label>
                    <select class="form-control" v-model="form.year" name="" id="">
                        <option v-for="item, i in years" :key="i" :value="item._id">{{ item.year }}</option>
                    </select>
                </b-form-group>
                <b-form-group>
                    <label for="">Kilometre</label>
                    <b-form-input v-model="form.km" id="input-horizontal"></b-form-input>
                </b-form-group>
                <b-form-group>
                    <label for="">Vites Tipi</label>
                    <select class="form-control" v-model="form.gear" name="" id="">
                        <option v-for="item, i in gears" :key="i" :value="item._id">{{ item.name }}</option>
                    </select>
                </b-form-group>
                <b-form-group>
                    <label for="">Yakıt Tipi</label>
                    <select class="form-control" v-model="form.fuel" name="" id="">
                        <option v-for="item, i in fuels" :key="i" :value="item._id">{{ item.name }}</option>
                    </select>
                </b-form-group>
                <b-form-group>
                    <label for="">Kasa Tipi</label>
                    <select class="form-control" v-model="form.case" name="" id="">
                        <option v-for="item, i in cases" :key="i" :value="item._id">{{ item.name }}</option>
                    </select>
                </b-form-group>

            </div>
            <div class="col-md-6">
                <b-form-group>
                    <label for="">Çekiş Türü</label>
                    <select class="form-control" v-model="form.traction" name="" id="">
                        <option v-for="item, i in tractions" :key="i" :value="item._id">{{ item.name }}</option>
                    </select>
                </b-form-group>
                <b-form-group>
                    <label for="">Motor Kapasitesi</label>
                    <b-form-input v-model="form.engine_capacity" id="input-horizontal"></b-form-input>
                </b-form-group>
                <b-form-group>
                    <label for="">Motor Gücü</label>
                    <b-form-input v-model="form.engine_power" id="input-horizontal"></b-form-input>
                </b-form-group>
                <b-form-group>
                    <label for="">Yakıt Tüketimi</label>
                    <b-form-input v-model="form.fuel_cons" id="input-horizontal"></b-form-input>
                </b-form-group>
                <b-form-group>
                    <label for="">Yakıt Deposu</label>
                    <b-form-input v-model="form.fuel_tank" id="input-horizontal"></b-form-input>
                </b-form-group>
                <b-form-group>
                    <label for="">Kimden</label>
                    <select class="form-control" v-model="form.fromWho" name="" id="">
                        <option v-for="item, i in fromWhoes" :key="i" :value="item._id">{{ item.name }}</option>
                    </select>
                </b-form-group>
                <b-form-group>
                    <label for="">Şehir</label>
                    <select class="form-control" v-model="form.city" @change="getDistrict" name="" id="">
                        <option v-for="item, i in cities" :key="i" :value="item._id">{{ item.city }}</option>
                    </select>
                </b-form-group>
                <b-form-group v-if="isVisibiltyDistricts">
                    <label for="">İlçe</label>
                    <select class="form-control" v-model="form.district" @change="getStreet" name="" id="">
                        <option v-for="item, i in districts.districts" :key="i" :value="item._id">{{ item.district }}
                        </option>
                    </select>
                </b-form-group>
                <b-form-group v-if="isVisibiltyStreets">
                    <label for="">Mahalle</label>
                    <select class="form-control" v-model="form.street" name="" id="">
                        <option v-for="item, i in streets.streets" :key="i" :value="item._id">{{ item.street }}
                        </option>
                    </select>
                </b-form-group>
                <b-form-group>
                    <label for="">Fiyat</label>
                    <b-form-input v-model="form.price" id="input-horizontal"></b-form-input>
                </b-form-group>
            </div>
        </div>
        <h5>İletişim Bilgileri</h5>
        <hr>
        <div class="row">
            <div class="col-md-6">
                <b-form-group>
                    <label for="">Ad Soyad</label>
                    <b-form-input v-model="form.contact_name"  id="input-horizontal"></b-form-input>
                </b-form-group>
            </div>
            <div class="col-md-6">
                <b-form-group>
                    <label for="">Telefon</label>
                    <b-form-input v-model="form.contact_phone" id="input-horizontal"></b-form-input>
                </b-form-group>
            </div>
        </div>
        <hr>
        <div class="row">
            <div class="d-flex w-100 justify-content-end">
                <b-button @click="addCar()"  class="add-btn">Ekle</b-button>
            </div>
        </div>
    </div>
</template>

<script>
import { loadavg } from 'os'

export default {
    data() {
        return {
            form: {},
            years: [],
            fuels: [],
            gears: [],
            cases: [],
            tractions: [],
            fromWhoes: [],
            categories: [],
            brands: [],
            models: [],
            cities: [],
            districts: [],
            streets: [],
            isVisibiltyBrands: false,
            isVisibiltyModels: false,
            isVisibiltyDistricts: false,
            isVisibiltyStreets: false,
        }
    },
    created() {
        this.getYear()
        this.getFuel()
        this.getGear()
        this.getCase()
        this.getTraction()
        this.getFromWho()
        this.getCategory()
        this.getCity()
    },
    methods: {
        async addCar() {
            await this.$axios.post("http://localhost:5000/api/car/add",this.form)
                .then((result) => {
                    console.log(result);
                    window.onload()
                }).catch((err) => {
                    console.log(err);
                });
        },
        getCategory() {
            this.$axios.get("http://localhost:5000/api/category")
                .then((result) => {
                    this.categories = result.data
                }).catch((err) => {

                });

        },
        getBrand() {
            this.isVisibiltyBrands = true
            this.$axios.get(`http://localhost:5000/api/category/${this.form.category}`)
                .then((result) => {
                    this.brands = result.data;
                }).catch((err) => {

                });
        },
        getModel() {
            this.isVisibiltyModels = true
            this.$axios.get(`http://localhost:5000/api/brand/${this.form.brand}`)
                .then((result) => {
                    this.models = result.data;
                }).catch((err) => {

                });
        },
        getCity() {
            this.$axios.get("http://localhost:5000/api/city")
                .then((result) => {
                    this.cities = result.data
                }).catch((err) => {

                });
        },
        getDistrict() {
            this.isVisibiltyDistricts = true
            this.$axios.get(`http://localhost:5000/api/city/${this.form.city}`)
                .then((result) => {
                    this.districts = result.data
                }).catch((err) => {

                });
        },
        getStreet() {
            this.isVisibiltyStreets = true
            this.$axios.get(`http://localhost:5000/api/district/${this.form.district}`)
                .then((result) => {
                    console.log(this.form);
                    this.streets = result.data
                }).catch((err) => {

                });
        },
        getYear() {
            this.$axios.get("http://localhost:5000/api/year")
                .then((result) => {
                    this.years = result.data
                }).catch((err) => {

                });

        },
        getFuel() {
            this.$axios.get("http://localhost:5000/api/fuel")
                .then((result) => {
                    this.fuels = result.data
                }).catch((err) => {

                });

        },
        getGear() {
            this.$axios.get("http://localhost:5000/api/gear")
                .then((result) => {
                    this.gears = result.data
                }).catch((err) => {

                });

        },
        getCase() {
            this.$axios.get("http://localhost:5000/api/case")
                .then((result) => {
                    this.cases = result.data
                }).catch((err) => {

                });

        },
        getTraction() {
            this.$axios.get("http://localhost:5000/api/traction")
                .then((result) => {
                    this.tractions = result.data
                }).catch((err) => {

                });

        },
        getFromWho() {
            this.$axios.get("http://localhost:5000/api/fromwho")
                .then((result) => {
                    this.fromWhoes = result.data
                }).catch((err) => {

                });

        },
    }

}
</script>

<style scoped>
.add-btn {
    border: none;
    background-color: #992726;
    color: #fff;
    padding: 10px 25px;
    border-radius: 10px;
    box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
    margin: 20px;
}

.add-btn:disabled {
    border: none;
    background-color: #d6d6d6;
    color: #000;
    cursor: no-drop;
    padding: 10px 25px;
    border-radius: 10px;
    box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
    margin: 20px;
}
</style>