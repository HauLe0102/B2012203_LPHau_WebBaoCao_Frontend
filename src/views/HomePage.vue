<script>
import ProductService from '../services/Product.service';
import StoreService from '../services/Store.service';
import SliderIProduct from '../components/SliderProduct.vue'

export default {
    components: {
        SliderIProduct
    },
    data() {
        return {
            ProductData: [],
            ProductDataSort: [],
            SellquantityProduct: []
        }
    },
    methods: {
        async getDataProduct() {
            try {
                this.ProductData = await ProductService.getProductLimit();
            } catch (error) {
                console.log(error)
            }
        },
        async getProductDataSort() {
            try {
                this.ProductDataSort = await StoreService.getStoreSort();
                console.log(this.ProductDataSort)
            } catch (err) {
                console.log(err);
            }
        },
    },
    mounted() {
        this.getDataProduct();
        this.getProductDataSort();
    },

}
</script>

<template>
    <div class="container" id="main_page">
        <!-- Slider Image -->
        <SliderIProduct></SliderIProduct>

        <!-- Main_Content_Product-->
    </div>
</template>

<style>
#main_page {
    height: 100%;
}

.item_product h4 {
    background-color: #62ab00;
    border-radius: 5px;
    text-align: center;
    color: white;
    padding: 5px;
    margin-bottom: 19px;
}

.item_product {
    border: 1.5px solid #62ab00;
    border-radius: 5px;
    padding: 5px;
}

.card-title {
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    line-clamp: 2;
    -webkit-box-orient: vertical;
}

#btn_detail {
    background-color: #62ab00;
    width: 100%;
    font-weight: bold;
    color: white;
}

/* CSS */
.button-88 {
    display: flex;
    align-items: center;
    font-family: inherit;
    font-weight: 500;
    font-size: 16px;
    padding: 0.7em 1.4em 0.7em 1.1em;
    color: white;
    background: #ad5389;
    background: linear-gradient(0deg, rgba(20, 167, 62, 1) 0%, rgba(102, 247, 113, 1) 100%);
    border: none;
    box-shadow: 0 0.7em 1.5em -0.5em #14a73e98;
    letter-spacing: 0.05em;
    border-radius: 20em;
    cursor: pointer;
    user-select: none;
    -webkit-user-select: none;
    touch-action: manipulation;
}

.button-88:hover {
    box-shadow: 0 0.5em 1.5em -0.5em #14a73e98;
}

.button-88:active {
    box-shadow: 0 0.3em 1em -0.5em #14a73e98;
}
</style>