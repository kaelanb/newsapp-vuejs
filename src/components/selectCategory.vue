<template>
    <div class="container is-semi-fluid">
        <div class="notification">
            <p class="heading"> <i class="fa fa-list"></i> Select A Category</p>
            <div class="field has-addons">
                <div class="control is-expanded">
                    <div class="select is-fullwidth">
                        <select name="cat" @change="categoryChanged">
                            <option v-for="(category,index) in categories" :key="index" :value="category.name">{{category.name}} </option>
                        </select>
                    </div>
                </div>
                <div class="control">
                    <button class="button is-danger" v-on:click="categoryChanged" >Get News</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

    export default{
        name: 'selectCategory',
        data (){
            return {
                categories: [
                    { id: 0, name: 'General' },
                    { id: 1, name: 'Technology' },
                    { id: 2, name: 'Business' },
                    { id: 3, name: 'Entertainment' },
                    { id: 4, name: 'Health' },
                    { id: 5, name: 'Science' },
                    { id: 6, name: 'Sports' }
                ]
            }
        },
        methods:{
            categoryChanged:function(evt){
                var that=this;
                Object.values(this.categories).map(function(elem,index){
                    if(elem.name==evt.target.value){
                        that.category=elem;
                    }
                  
                });
                if(!that.category){
                    this.$emit('newCategory', 'General'); 
                }
                this.$emit('newCategory', this.category.name);
            }
        }
    }
</script>

<style>

.is-semi-fluid{
    margin-bottom: 20px;
}

@media (min-width: 600px){
    .is-semi-fluid{
        width:70%;
    }    
}
</style>