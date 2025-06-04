<script setup>

    import { ref, onMounted } from 'vue';
    import axios, { Axios } from 'axios';


    import ProductCard from './component/ProductCard.vue';
    import EmptyCard from './component/EmptyCard.vue';

    const Products = ref([]);
    onMounted(()=>{

        axios.get('https://dummyjson.com/products')
        .then(function (response) {
            // handle success
            Products.value=response.data.products;
        });
    });


</script>

<template>

  <!-- chat list -->
  <div class="chat-list">
        <div class="header">
            <h2>
                <img class="network" src="./images/chat-list/chat-list/network.svg" alt="network">
                <span>Products ({{ Products.length }})</span>
            </h2>
            <div class="action">
                <span><img src="./images/chat-list/theme.svg" alt="theme"></span>
                <span><img src="./images/chat-list/add.svg" alt="add"></span>
            </div>
        </div>

        <div class="search">
            <img src="./images/chat-list/search.svg" alt="search">
            <input type="text" placeholder="Search in products">
        </div>

        <ul v-if="ProductLoading">
          <li style="justify-content: center;height: 100%;">
            <img style="width: 100px;" src="./images/loader.gif" alt="">
          </li>
        </ul>

        <ul v-else>
            <ProductCard v-for="product in Products" :key="product.id" 
                        :product="product" />
            
            <EmptyCard v-if="Products.length == 0" />            
        </ul>
    </div>
    <!-- chat list -->

</template>