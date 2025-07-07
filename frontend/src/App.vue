<template>
  <div class="header">
    <span>CROMA HEADER</span>
  </div>
  <div>
    <h1>Croma Televisions & Accessories - Product Cards</h1>
    <div class="product-grid">
      <div v-for="product in products" :key="product.product_id" class="product-card">
        <h3>{{ product.title }}</h3>
        <p>Price: {{ product.price }}</p>
        <p>Sale Price: {{ product.sale_price }}</p>
        <p>{{ product.discount_message }}</p>
      </div>
    </div>
  </div>
</template>


<script>
export default {  
  data() {
    return {
      products: [] // This will hold the products fetched from the backend
    }
  },
  mounted() {
    // Fetch the products from the backend service using fetch API
    // Store the products in the products data property created above
    fetch('http://localhost:5000/products')
      .then(res => res.json())
      .then(data => {
        this.products=data;
      })
  }
}
</script>

<style>
.header {
  background-color: #000;
  padding: 20px;
  text-align: center;
  font-size: 24px;
  font-weight: bold;
  span {
    color: #fff;
  }
}
.product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 24px;
  margin: 24px 0;
  padding: 0 16px;
}

.product-card {
  background: #fff;
  border: 1px solid #e0e0e0;
  border-radius: 12px;
  padding: 20px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
  transition: box-shadow 0.2s;
}
.product-card:hover {
  box-shadow: 0 4px 16px rgba(0,0,0,0.12);
}

</style>



