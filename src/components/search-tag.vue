<template>
<div class="my-4 bg-own py-4 px-4">
    <div class="row">
        <div class="col">
            <h3>Filter Items</h3>
        </div>
    </div>
    <div class="input-group mb-3">
        <input type="text" class="form-control" placeholder="Search Product by Name..." aria-label="Search" v-model="searchName" v-on:keyup="filterSearch()">
    </div>
    <hr>
    <div class="row">
        <div class="col text-center">
            <h3>Tags</h3>
        </div>
    </div>
    <div class="container row mx-2">
        <div class="col-4 form-group" v-for="(category, index) in categories" v-bind:key="index">
            <input type="checkbox" class="form-check-input" v-bind:id="getID(index)" v-bind:value="getValue(category)" v-model="tempCat" v-on:change="checkedItems">
            <label class="form-check-label" v-bind:for="getID(index)">{{ category }}</label>
        </div>
    </div>
</div>
</template>
    
<script>
export default {
    name: 'search-tag',
    props: {
        categories: {
            type: Array
        }
    },
    methods: {
        getID(index) {
            return index;
        },
        filterSearch() {
            this.$emit('filter-search', this.searchName);
        },
        getValue(value) {
            return value;
        },
        checkedItems() {
            this.$emit('check-item', this.tempCat);
        }

    },
    data() {
        return {
            searchName: '',
            tempCat: [],
        }
    }
}
</script>

