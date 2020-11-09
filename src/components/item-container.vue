<template>
<div class="col py-4 px-4">
<div class="row">
    <div class="col">
        <h3>Available Items</h3>
    </div>
</div>
<div class="row px-4 myScroll">
    <div>
        <div class="card row border-0" v-for="(product, index) in products" v-bind:key="index" v-on:click="getDetails(product, getColor(index))">
            <div v-bind:class="getColor(index)">
                <div class="card-header h3">{{ product.productName }}</div>
                <div class="card-body row">
                    <div class="col">
                        <img class="card-img" v-bind:src="getURL(product.url)" alt="Card image cap">
                    </div>
                    <div class="col">
                        <p class="card-text"><span style="font-weight: bold;">Product Price:</span> {{ product.price }}</p>
                        <p class="card-text"><span style="font-weight: bold;">Product Description:</span> {{ product.description }}</p>
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
    name: 'item-container',
    props: {
        products: {
            type: Array
        }
    },
    data() {
        return {
            custom: ['card text-white bg-primary mb-3', 'card text-white bg-secondary mb-3', 'card text-white bg-success mb-3', 'card text-white bg-danger mb-3', 'card text-white bg-warning mb-3', 'card text-white bg-info mb-3', 'card text-white bg-dark mb-3'],
        }
    },
    methods: {
        getURL(url) {
            return url; 
        },
         getColor(index) {
            return this.custom[index % this.custom.length];
        },
        getDetails(product, color) {
            product.class = color;
            this.$emit('show-details', product);
        }

    }
}
</script>


<style scoped>
.myScroll {
    overflow-y: scroll;
    height: 940px;
    overflow-x: hidden;

}

/* width */
.myScroll::-webkit-scrollbar {
  width: 10px;
}

.card {
    -webkit-filter: brightness(100%);
    cursor: pointer;
}
.card:hover > div {
     -webkit-filter: brightness(95%);
    -webkit-transition: all .3s ease;
    -moz-transition: all .3s ease;
    -o-transition: all .3s ease;
    -ms-transition: all .3s ease;
    transition: all .3s ease;
}

/* Track */
.myScroll::-webkit-scrollbar-track {
  background: #f1f1f1; 
}
 
/* Handle */
.myScroll::-webkit-scrollbar-thumb {
  background: #01becc; 
}

/* Handle on hover */
.myScroll::-webkit-scrollbar-thumb:hover {
  background: #009ba7; 
}
</style>

