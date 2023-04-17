<template>
    <div class="review-form">
        <h3>Leave a Review</h3>
        <form @submit.prevent="onSubmit">
        <label for="name">Name</label>
        <input type="text" id="name" v-model="name" />
        <label for="review">Review</label>
        <textarea id="review" v-model="review" />
        <label for="rating">Rating</label>
        <select id="rating" v-model.number="rating">
            <option>5</option>
            <option>4</option>
            <option>3</option>
            <option>2</option>
            <option>1</option>
        </select>
        <input class="button" type="submit" value="Submit" />
        </form>
    </div>
</template>

<script>
    export default {
        name: 'ReviewForm',
        data() {
            return {
                name: '',
                review: '',
                rating: null
            }
        },
        props: {
            reviews: {
                type: Array,
                required: true
            },
            identity: {
                type: Number,
                required: true
            }
        },
        methods: {
            onSubmit() {
                if (this.name === '' || this.rating === null || this.review === '') {
                    alert('Review is incomplete. Please fill out every field.')
                    return
                }
                let review = {
                    name: this.name,
                    review: this.review,
                    rating: this.rating
                }
                this.$emit('review-submitted', review, this.identity)
                this.name = ''
                this.review = ''
                this.rating = null
            }
        }
    }
</script>