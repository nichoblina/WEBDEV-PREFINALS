<template>
    <main id="details">
        <div class="container mt-4">
            <div class="row">
                <div class="card text-center">
                    <img :src="$route.query.img" class="card-img-top mx-auto mt-4" alt="">
                    <div class="card-body">
                        <h1 class="mb-3 fw-bolder">{{ $route.query.name }}</h1>
                        <p class="mb-3"><span>Category: </span>{{ $route.query.category }}</p>
                        <p class="mb-3"><span>Description: </span>{{ $route.query.description }}</p>
                        <p class="mb-3"><span>Quantity: </span>{{ $route.query.quantity }}</p>
                        <p class="mb-3"><span>Price: </span>P{{ $route.query.price }}</p>
                        <div class="d-grid gap-2 d-md-block">
                            <button class="btn-danger mx-2" @click="minus">-</button>
                            <input type="number" v-model="qtyChoice" class="text-center">
                            <button class="btn-success mx-2" @click="plus">+</button>
                        </div>
                        <div class="mt-2">
                            <router-link to="/about"><button class="btn-primary" @click="addToCart">Add to Cart</button></router-link>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>

<script>

export default {
    name: 'Details',
    data() {
        return {
            qtyChoice: 0
        }
    },
    methods: {
        minus() {
            if (this.qtyChoice > 0) {
                this.qtyChoice--
            }
        },
        plus() {
            if (this.qtyChoice < this.$route.query.quantity) {
                this.qtyChoice++
            }
        },
        addToCart() {
            const childData = {
                name: this.$route.query.name,
                price: (this.$route.query.price * this.qtyChoice),
                quantity: this.qtyChoice,
                img: this.$route.query.img
            };
            this.$route.query.quantity -= this.qtyChoice
            console.log(childData)
            this.$emit('add-to-cart', childData)
        }
    }
}

</script>