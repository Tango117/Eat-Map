<template>
    <div class="review-list">
        <h4>Reviews</h4>
        <div v-if="!reviews.length">There are no reviews yet.</div>
        <ul>
            <li v-for="(review, index) in reviews" :key="index">
                <p>{{ review.name }}</p>
                <p>Rating: {{ review.rating }}</p>
                <p>Review: {{ review.reviewText }}</p>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: 'ReviewList',
        props: {
            reviews: {
                type: Array,
                required: true
            }
        }
    }
</script>