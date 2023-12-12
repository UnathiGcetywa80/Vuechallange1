<template>
  <div>
      <input type="text" v-model="searchQuery" placeholder="Search by product name" />
      <select v-model="selectedCategory">
        <option value="">Cheap</option>
        <option value="">Expensive</option>
        <option v-for="category in uniqueCategories" :key="category" :value="category">
          {{ category }}
        </option>
      </select>
    </div>
  <div class="wrapper">
    <div class="row" v-if="products.length">
      <div class="prodCard" v-for="product in products" :key="product.id">
        <div class="card-header">
          <h3>{{ product.Name }}</h3>
        </div>
        <img @mouseenter="onMouseEnter" @mouseleave="onMouseLeave" :src="product.image" :alt="product.Name" loading="lazy" />
        <p :class="product.amount > 2000 ? 'expensive' : 'cheap'">R{{ product.amount }}</p>
      </div>
      <div class="card-footer">
        <a href="#" type="button">View Details</a>
      </div>
    </div>
    <div v-else>
      <h2>No products found.</h2>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      products: [
        {
          id: 6,
          Name: "CH253 Black S.T Men's Shoes",
          amount: 2350.00,
          image: "https://i.postimg.cc/rFJnFmB2/0004027-chekich-ch253-bt-erkek-ayakkabi-siyah-1200x1800-1200x1800.jpg",
          
        },
        {
          id: 2,
          Name: "CH169 CBT Thorn Men Sneaker White",
          amount: 3999.99,
          image: "https://i.postimg.cc/y8xTvdLY/0005324-chekich-ch169-bt-erkek-ayakkabi-beyaz.webp"
          
        },
        {
          id: 5,
          Name: "Chekich All White Honcho",
          amount: 1999.99,
          image: "https://i.postimg.cc/L8HvZptK/edf35b-efb17f86696d4430932d0d619fed26d6-mv2.webp"
          
        },
        {
          id: 4,
          Name: "CH149 CBT Changer Over Men Sneaker Tan",
          amount: 2999.99,
          image: "https://i.postimg.cc/W3QFg4xf/sneaker-1.webp"
          
        },
        {
          id: 3,
          Name: "Sneaker White",
          amount: 2599.99,
          image: "https://i.postimg.cc/9Fnmw8Sg/0004387-chekich-ch033-bt-erkek-ayakkabi-beyaz.webp"
          
        },
        {
          id: 1,
          Name: "CH253 CBT Mirror Non Men Sneaker White",
          amount: 3000.00,
          image: "https://i.postimg.cc/rmwnXJJx/0007253-ch253-cbt-mirror-non-erkek-ayakkabi-beyaz.webp",
          
          
        },
      ],
      selectedCategory: '',
      searchQuery: ''
    }
  },

  computed() { },
  methods: {
    onMouseEnter() {
      alert("Thank you");
    },
    onMouseLeave() {
      alert("Bye");
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.wrapper :is(.row) {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.prodCard {
  width: 15rem;
}

.prodCard :is(> *, img) {
  width: 100%;
  aspect-ratio: 1/1;
}

.expensive {
  font-weight: bolder;
  color: darkkhaki;
}

.cheap {
  color: black;
}
</style>
