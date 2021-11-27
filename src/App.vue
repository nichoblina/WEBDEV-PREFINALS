<template>
  <div id="nav" class="container d-flex justify-content-center">
    <router-link to="/" class="mx-3">Menu</router-link> |
    <router-link to="/about" class="mx-3">Cart</router-link>
  </div>
  <router-view @add-to-cart="addToCart" :parentData="parentData" :appFood="appFood"/>
</template>

<script>

export default {
  name: 'App',
  components: {

  },

  data() {
    return {
      parentData: [],
      appFood: [
                {id: 1, name: "Bacon",price:250,quantity:32, description: "a type of salt-cured pork made from various cuts, typically the belly or less fatty parts of the back.", category: ["Meat"],img:'https://healthyrecipesblogs.com/wp-content/uploads/2018/01/oven-bacon-featured.jpg'},
                {id: 2, name: "Fish",price:150,quantity:8, description: "a type of meat that is an important source of protein and other nutrients", category: ["Seafood","Fresh"],img:'https://cdn-prod.medicalnewstoday.com/content/images/articles/322/322522/fresh-fish-on-ice.jpg'},
                {id: 3, name: "Chicken",price:200,quantity:9, description: "a type of poultry that is highly nutritious and a good source of protein.", category: ["Poultry","Fresh"],img:'https://www.seriouseats.com/thmb/t82X6N4ZwGkFZmWPuCjwT-osL3g=/1500x844/smart/filters:no_upscale()/20210714-potato-starch-fried-chicken-vicky-wasik-seriouseats-20-17e193a6bf274bba9091810a0b18ef89.jpg'},
                {id: 4, name: "Beef",price:300,quantity:0, description: "a type of meat that is high in protein and rich in minerals", category: ["Meat"],img:'https://post.healthline.com/wp-content/uploads/2020/08/beef-update-1200x628-facebook-1200x628.jpg'},
                {id: 5, name: "Soy Sauce",price:50,quantity:42, description: "a salty liquid condiment traditionally produced by fermenting soybeans and wheat", category: ["Sauce","Seasoning"],img:'https://www.tasteofhome.com/wp-content/uploads/2020/01/GettyImages-461879075.jpg?fit=700,1024'},
                {id: 9, name: "Egg",price:10,quantity:22, description: "a chicken's egg which is comprised of many nutrients", category: ["Dairy"],img:'https://cdn.britannica.com/94/151894-050-F72A5317/Brown-eggs.jpg'},
                {id: 11, name: "Pork",price:200,quantity:4, description: "a type of meat that comes from a pig and provides savory tastes", category: ["Meat"],img:'https://www.seriouseats.com/thmb/yHg0KQZc928Iqbm8G-aOE91gJb0=/1500x1125/filters:fill(auto,1)/__opt__aboutcom__coeus__resources__content_migration__serious_eats__seriouseats.com__recipes__images__2016__02__20160208-sous-vide-pork-chop-guide-food-lab-37-9bfa2f9b8a464bccad99ea08423b9d8e.jpg'},
            ]
    }
  },

  methods: {
    addToCart(childData) {
      console.log(childData)
      this.parentData.push(childData)
    }
  }
}

</script>

<style>

.container {
  font-family: "Montserrat", sans-serif;
  font-weight: bold;
}

#nav {
  padding: 30px;
}

#nav a {
  font-family: "Montserrat", sans-serif;
  font-size: 20px;
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: white;
}

</style>
