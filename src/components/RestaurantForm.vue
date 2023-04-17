<template>
    <div class="restaurant-form">
        <h3>Add a Restaurant</h3>
        <form @submit.prevent="onSubmit">
        <label for="name">Name</label>
        <input type="text" id="name" v-model="name" />
        <label for="cuisine">Cuisine</label>
        <input type="text" id="cuisine" v-model="cuisine" />
        <label for="price">Price</label>
        <select id="price" v-model.number="price">
            <option>$$$$</option>
            <option>$$$</option>
            <option>$$</option>
            <option>$</option>
        </select>
        <input class="button" type="submit" value="Submit" />
        </form>
    </div>
</template>

<script>
    export default {
        name: 'RestaurantForm',
        data() {
            return {
                name: '',
                cuisine: '',
                price: null
            }
        },
        props: {
            restaurants: {
                type: Array,
                required: true
            }
        },
        methods: {
            onSubmit() {
                if (this.name === '' || this.price === null || this.cuisine === '') {
                    alert('Restaurant Data is incomplete. Please fill out every field.')
                    return
                }
                let restaurant = {
                    name: this.name,
                    price: this.price,
                    cuisine: this.cuisine,
                    reviews: [],
                    reviewFormVisible: false
                }
                this.$emit('restaurant-submitted', restaurant)
                this.name = ''
                this.cuisine = ''
                this.price = null
            }
        }
    }
</script>