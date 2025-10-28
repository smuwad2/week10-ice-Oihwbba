<script>
import blogPost from './subcomponents/BlogPost2.vue'
import axios from 'axios'

export default {
    components: { blogPost },
    data() {
        return {
            posts: [] // array of post objects
        }  
    },
    computed: {
        baseUrl() {
            if (window.location.hostname === 'localhost')
                return 'http://localhost:3000'
            else {
                const codespace_host = window.location.hostname.replace('5173', '3000')
                return `https://${codespace_host}`
            }
        }
    },
    created() {
        axios.get(`${this.baseUrl}/posts`)
        .then(response => {
            this.posts = response.data
            console.log(response.data)
        })
        .catch(error => {
            this.posts = [{ entry: 'There was an error: ' + error.message }]
        })
    },
    methods: {
        deletePost(id) {
            axios.get(`${this.baseUrl}/deletePost`, { params: { id } })
            .then(response => {
                console.log(response.data.message)
                // Remove the deleted post from local list
                this.posts = this.posts.filter(post=>post.id!=id)
            })
            .catch(error => {
                console.error(error)
            })
        }
    }
}
</script>

<template>
    <div>
        <blogPost 
            v-for="post in posts"
            :key="post.id"
            :subject="post.subject"
            :entry="post.entry"
            :mood="post.mood"
        >
            <button class="btn btn-primary" @click="deletePost(post.id)">
                Delete
            </button>
       
        </blogPost>
    </div>
</template>
