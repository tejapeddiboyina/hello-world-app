<template>
    <div>
        <div v-if="isEligibleFreeVouvher">
            <h1>Congrats!! You are eligible for a free voucher</h1>
        </div>

        </br>
        <div>
            {{itemsInCart}} - items in cart
        </div>
        <div v-for="prod in listOfProducts" :key="prod.name">
            <input v-model="selectedProduct" type="checkbox" :value="prod.name">{{prod.name | toCaps}}  - {{prod.desc}}</input>
        </div>

        <br/>
        <div>
            Selected Product - {{selectedProduct}}
        </div>

        <br/>
        <input type="button" @click="GetSelectedProducts()" value="Get Selected Products"/>
    </div>

</template>

<script>
export default {
    name:'HelloWorldProductList',
    props:{
        listOfProducts :{
            required : true
        }

    },
    data(){
        return {
            selectedProduct:[],
            isEligibleFreeVouvher: false
        }
    },
    computed: {
        itemsInCart(){
            return this.selectedProduct.length;
        }
    },
    methods: {
        GetSelectedProducts(){
           this.$emit('hw-selectedproduct', this.selectedProduct);
        }
    },
    watch: {
        selectedProduct :{
            handler(value, oldValue){
                if(value.length===this.listOfProducts.length){
                    this.isEligibleFreeVouvher = true;
                }
            }
        }
    }



}


</script>