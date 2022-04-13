<template>
  <div>
    <div class = "card" style="width: 18rem;" v-for = "product in products" :key = "product.id">

<figure>
        <img v-bind:src="product.img" style = "border-bottom: 1px solid black" class="card-img-top"/>
      </figure>
      <h4 class="card-title">{{product.title}}</h4>
      <p class="card-text">Location {{ product.location }}</p>
      <p class="card-text">Price: {{ product.price }}</p>
      <p class="card-text">Availability: {{ product.availableSlots }}</p>
      <button class="btn btn-primary" @click="add(product)">Add to cart</button>
    </div>
  </div>

</template>

<script>
export default {
  name: "ProductList",
  data() {
    return {
      products: [
        {
        id: 1001,
        title: "Literature",
        price: 50,
        location: "Leicester",
        img: "pen.png",
        availableSlots: 5
       },
        {
        id: 1002,
        title: "Algebra",
        price: 80,
        location: "Chelsea",
        img: "math.png",
        availableSlots: 5
        },
        {
        id: 1003,
        title: "Art",
        price: 40,
        location: "Lincoln",
        img: "art.webp",
        availableSlots: 5
        },
    {
        id: 1004,
        title: "Drama",
        price: 110,
        location: "Birmingham",
        img: "drama.jpg",
        availableSlots: 5
    },

    {
        id: 1005,
        title: "English Creative Writing",
        price: 95,
        location: "Liverpool",
        img: "creative.jpg",
        availableSlots: 5
    },
    {
        id: 1006,
        title: "Music",
        price: 55,
        location: "Newcastle",
        img: "music.jpg",
        availableSlots: 5
    },
    {
        id: 1007,
        title: "German Language",
        price: 84,
        location: "Liverpool",
        img: "german.webp",
        availableSlots: 5
    },
    {
        id: 1008,
        title: "French Language",
        price: 80,
        location: "Bradford",
        img: "french.jpg",
        availableSlots: 5
    },
    {
        id: 1009,
        title: "Martial Arts",
        price: 70,
        location: "Chelsea",
        img: "martial.jpg",
        availableSlots: 5
    },
    {
        id: 1010,
        title: "Dance",
        price: 115,
        location: "Birmingham",
        img: "dance.jpg",
        availableSlots: 5
      },


      ],
    };
  },

  methods: {
    // adding the product function
    add(product) {
      console.log("added product", product.id);
      this.$emit('addProduct',product);
    },

    // this function returns the number of subjects in the cart
    cartCount(id){
          let count = 0;
          for (let i = 0; i < this.products.length; i++) {
            if (this.products[i].id === id) {
              count++;
            }
          }
          return count;
    } 
  },
};
</script>