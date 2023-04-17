<template>
    <div class="restaurant-display">
        <ul>
            <li v-for="(restaurant, index) in restaurants" :key="index">
                <div class="review-container">
                    <h3>{{ restaurant.name }}</h3>
                    <p>{{ restaurant.cuisine }} {{ restaurant.price }}</p>
                    <!-- <button class="button" @click="toggleReviewForm">Add Review</button> -->
                    <ReviewList :reviews="restaurant.reviews"></ReviewList>
                    <ReviewForm :identity="index" @review-submitted="addReview"></ReviewForm>
                    <!-- v-show="restaurant.reviewFormVisible" -->
                    <!-- <review-list :reviews="reviews"></review-list> -->
                </div>
                <!-- <ReviewForm v-show="restaurant.reviewFormVisible" @review-submitted="addReview"></ReviewForm> -->
                <!-- <review-form v-show="reviewFormVisible" @review-submitted="addReview"></review-form> -->
            </li>
        </ul>
        <RestaurantForm @restaurant-submitted="addRestaurant"></RestaurantForm>
    </div>
</template>

<script>
    import ReviewList from './ReviewList.vue'
    import ReviewForm from './ReviewForm.vue'
    import RestaurantForm from './RestaurantForm.vue'
    export default {
        name: 'RestaurantList',
        components: {
            ReviewList,
            ReviewForm,
            RestaurantForm
        },
        data() {
            return {
                restaurants: [
                    {
                        name: 'Arte Bistro',
                        cuisine: 'French',
                        price: '$$$',
                        reviews: [],
                        reviewFormVisible: false
                    },
                    {
                        name: 'Five Guys',
                        cuisine: 'American',
                        price: '$',
                        reviews: [],
                        reviewFormVisible: false
                    }
                ]
            }
        },
        methods: {
            addReview(review, id) {
                this.restaurants[id].reviews.push(review)
            },
            toggleReviewForm() {
                this.reviewFormVisible = !this.reviewFormVisible
            },
            addRestaurant(restaurant) {
                this.restaurants.push(restaurant)
            }
        }
    }
</script>
