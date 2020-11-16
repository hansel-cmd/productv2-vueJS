<template>
  <div class="container  my-4">
    <div class="row my-4">
      <div class="col-lg-6 bg-light border-right">
        <searchTag v-bind:categories="category" v-on:filter-search="filterSearch($event)" v-on:check-item="checkedItems($event)"></searchTag>

        <hr />

        <itemDetails v-bind:product="show"></itemDetails>
      </div>

       <div class="col-lg-6 bg-light">
          <itemContainer v-bind:products="filteredItems" v-on:show-details="showDetails($event)"></itemContainer>
       </div>
    </div>
  </div>
</template>

<script>
import itemContainer from '../components/item-container';
import searchTag from '../components/search-tag';
import itemDetails from '../components/item-details';

export default {
  name: "App",
  components: {
    itemContainer,
    searchTag,
    itemDetails
  },
  methods: {
    filterSearch(e) {
      this.searchName = e;
    },
    checkedItems(e) {
      this.tempCat = e;
    },
    showDetails(e) {
      this.itemDetails = e;
    },
  },
  computed: {
    show() {
      return this.itemDetails;
    },
    filteredItems() {
      let tags = [];

      this.products.forEach(item => {
        for (let i = 0; i < item.category.length; i++) {
          if (this.tempCat.includes(item.category[i])) {
            tags.push(item);
            break;
          }
        }
      });

      if (this.searchName == '') {
        return tags.length != 0 ? tags : this.products;
      }

      let x = this.products.filter(item => {
        return item.productName.toUpperCase().match(this.searchName.toUpperCase());
      });
      return x;
    }
  },
  data() {
    return {
      itemDetails: {},
      searchName: '',
      tempCat: [],
      category: ['Meat', 'Seafood', 'Fresh', 'Poultry', 'Sauce', 'Seasoning', 'Dairy', 'Utensils', 'Cookware'],
      products: [
        {
          id: 1,
          productName: "Bacon",
          price: '$10',
          url: "https://www.simplyrecipes.com/wp-content/uploads/2019/08/baked-bacon-Lead-1.jpg",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto dolorum fuga cupiditate reprehenderit facilis doloribus?",
          category: ["Meat"],
        },
        {
          id: 2,
          productName: "Fish",
          price: '$12',
          url: "https://www.thespruceeats.com/thmb/XGRJM0-tS0xcCRGMI1oomUQsENo=/450x0/filters:no_upscale():max_bytes(150000):strip_icc()/495287925-56a2f6f05f9b58b7d0cfe456.jpg",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto dolorum fuga cupiditate reprehenderit facilis doloribus?",
          category: ["Seafood", "Fresh"],
        },
        {
          id: 3,
          productName: "Chicken",
          price: '$14',
          url: "https://cdn.thealternativedaily.com/wp-content/uploads/2014/08/chicken-640x360.jpg",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto dolorum fuga cupiditate reprehenderit facilis doloribus?",
          category: ["Poultry", "Fresh"],
        },
        {
          id: 4,
          productName: "Beef",
          price: '$14',
          url: "https://previews.123rf.com/images/photovs/photovs1706/photovs170600212/80555447-raw-fresh-meat-beef-or-pork-in-supermarket-for-steak-ingredient-steaks-in-stores.jpg",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto dolorum fuga cupiditate reprehenderit facilis doloribus?",
          category: ["Meat"],
        },
        {
          id: 5,
          productName: "Soy Sauce",
          price: '$12',
          url: "https://image.made-in-china.com/202f0j00oCpRVlkFChcr/1-7L-Superior-Light-Soy-Sauce-for-Supermarket-with-Brc-Certificate.jpg",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto dolorum fuga cupiditate reprehenderit facilis doloribus?",
          category: ["Sauce", "Seasoning"],
        },
        {
          id: 6,
          productName: "Milk",
          price: '$8',
          url: "https://cdn.shopify.com/s/files/1/2597/8324/collections/citysuper-milk-collection_600x600.jpg?v=1527136268",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto dolorum fuga cupiditate reprehenderit facilis doloribus?",
          category: ["Dairy"],
        },
        {
          id: 7,
          productName: "Cheese",
          price:' $20',
          url: "https://cdn.cnn.com/cnnnext/dam/assets/200623110902-cheddar-cubes-full-169.jpg",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto dolorum fuga cupiditate reprehenderit facilis doloribus?",
          category: ["Dairy"],
        },
        {
          id: 8,
          productName: "Frying Pan",
          price: '$78',
          url: "https://images-na.ssl-images-amazon.com/images/I/818f4kPX-ZL._AC_SX522_.jpg",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto dolorum fuga cupiditate reprehenderit facilis doloribus?",
          category: ["Utensils", "Cookware"],
        },
        {
          id: 9,
          productName: "Egg",
          price: '$24',
          url: "https://www.wishtv.com/wp-content/uploads/2020/03/CROP-Eggs-hypatia-h_bcdda256340f68287a2e0ebced64dac0-h_b422392013797decae81d659f46ca31e.jpg",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto dolorum fuga cupiditate reprehenderit facilis doloribus?",
          category: ["Dairy"],
        },
        {
          id: 10,
          productName: "Plates",
          price: '$29',
          url: "https://images-na.ssl-images-amazon.com/images/I/418KI2pVE0L._AC_SL1000_.jpg",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto dolorum fuga cupiditate reprehenderit facilis doloribus?",
          category: ["Utensils"],
        },
        {
          id: 11,
          productName: "Pork",
          price: '$98',
          url: "https://media.istockphoto.com/photos/assortment-of-pork-meats-in-butcher-shops-showcase-in-supermarket-picture-id1198946162?k=6&m=1198946162&s=170667a&w=0&h=7rxIMV5_TL2ALz9lY2SkQJ7EdQxOnHjVWN7MtLQcgxw=",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto dolorum fuga cupiditate reprehenderit facilis doloribus?",
          category: ["Meat"],
        },
      ],
    };
  },
};
</script>
