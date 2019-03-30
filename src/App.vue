<template>
  <div id="app1">
    <img alt="Vue logo" src="./assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <hw-products :listOfProducts="productlist"
                @hw-selectedproduct="GetSelectedProductsInParent"/>

                <br>

    <div v-if="isSelectedProductVisible">
      <div v-if="selectedProductInParent.length >0">
        <div v-for="item in selectedProductInParent" :key="item">
          {{item}}
        </div>
        

    </div>
    <div v-else>
      No Items Selected
      </div>
      </div>
    
    <hw-footer/>
  </div>
  
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import HWorldFooter from '@/components/HWFooter.vue'
import HWProductList from '@/components/HWProductListing.vue'

export default {
  name: 'app',
  components: {
    'hw-footer': HWorldFooter,
    'hw-products': HWProductList
  },
  data(){
    return {
      productlist:[
        {name: 'Product A', desc: 'This is about Product A'},
        {name: 'Product B', desc: 'This is about Product B'},
        {name: 'Product C', desc: 'This is about Product C'},
        {name: 'Product D', desc: 'This is about Product D'}
      ],
      selectedProductInParent: [],
      isSelectedProductVisible: false
    }
  },
  methods: {
    GetSelectedProductsInParent(prodValue){
      this.selectedProductInParent = prodValue;
      this.isSelectedProductVisible = true;
    }
  }
}
</script>

<style>
#app1 {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
