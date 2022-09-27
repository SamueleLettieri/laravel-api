<template>
  <main>
    <div class="container">
        <CardPost v-for="post in posts" :key="post.id" :post="post"/>
    </div>
  </main>
</template>

<script>
import axios from "axios";
import CardPost from './CardPost.vue'
export default {
    components: {
        CardPost 
    },


    data: function(){
        return{
            posts : [],
            currentPagge : 1,
            lastPage : null,
            loading : false,
        }
    },

    methods: {
        getMovies(postsPage = 1) {
            axios.get( `/api/posts`, {page: postsPage})
                .then((response) => {
                console.log(response.data.results.data);
                this.posts = response.data.results.data;
                this.currentPagge = response.data.results.currentPagge;
                this.lastPage = response.data.results.lastPage;
                
            })
                .catch((error) => {
                console.warn(error);
            });
        },
    },
    created(){
        this.getMovies();
    }
}
</script>

<style>

</style>