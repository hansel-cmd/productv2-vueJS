<template>
<div class="col bg-own py-4 px-4">
<div class="row">
    <div class="col">
        <h3>Item Details</h3>
    </div>
</div>
<div class="card row" v-if="!checkIfEmpty()">
    <div v-bind:class="getClass(product)">
        <div class="card-header h3">{{ product.productName }}</div>
        <div class="card-body row">
            <img class="card-img my-2" v-bind:src="getURL(product.url)" alt="Card image cap">

            <p class="card-text"><span style="font-weight: bold;">Product Price:</span> {{ product.price }}</p>
            <p class="card-text"><span style="font-weight: bold;">Product Description:</span> {{ product.description }}</p>
            <p class="card-text"><span style="font-weight: bold;">Product Category: </span> {{ addComma }}</p>
            
        </div>
    </div>
</div>

<div class="card row" v-show="checkIfEmpty()">
    <div v-bind:class="getClass(product)">
        <div class="card-header h3"></div>
        <div class="card-body row">
            <img class="card-img my-2" src="https://vcunited.club/wp-content/uploads/2020/01/No-image-available-2.jpg" alt="Card image cap">
        </div>
    </div>
</div>


</div>
</template>

<script>
export default {
    name: 'item-details',
    props: {
        product: {
            type: Object
        },
        clickedMe: {
            type: Boolean
        }
    },
    methods: {
        getURL(url) {
            return url; 
        },
        checkIfEmpty() {
            return Object.keys(this.product).length === 0 
                    && this.product.constructor === Object ? true : false;
        },
        getClass(product) {
            return product.class;
        }
    },
    computed: {
        addComma() {
            console.log(this.product.category);
            if (!this.checkIfEmpty()) {
                let x = this.product.category.join(", ");
                return x;
            }
            return this.product.category;
        }
    }
}
</script>