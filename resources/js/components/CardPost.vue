<template>
<div class="container mt-5">
    <div class="card text-center">
        <div class="card-header">
            post
        </div>
        <div class="text-center">
            <img :src="`${post.post_image}`" class="card-img-top w-50 rounded-0 m-3" alt="{post.title}img">
        </div>    
        <div class="card-body">
            <h5 class="card-title m-3">{{post.user.name}}</h5>
            <h5 class="card-title m-3">
            <div v-for="tag in post.tags" :key="tag.id">
                {{tag.name}}
            </div>
            </h5>
            <h3 class="card-title m-3">{{post.title}}</h3>
            <p class="card-text m-3">{{post.post_content}}</p>
        </div> 
        <div class="card-footer text-muted ">
            {{post.post_date}}
        </div>
    </div>
</div>
</template>

<script>
export default {
props: ['post']
}
</script>

<style>

</style>