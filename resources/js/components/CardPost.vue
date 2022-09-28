<template>
<div class="container mt-5">
    <div class="card text-center">
        <div class="card-header">
            post
        </div>
        <div class="text-center">
            <img v-if="ValidURL(post.post_image)" :src="post.post_image" class="card-img-top w-50 rounded-0 m-3" alt="{post.title}img">
            <img v-else :src="'storage/' + post.post_image" class="card-img-top w-50 rounded-0 m-3" :alt="post.post_image">
        </div>    
        <div class="card-body">
            <h3 class="card-title m-3">{{post.user.name}}</h3>
            <h5 class="card-title m-3">
                <span v-for="tag in post.tags" :key="tag.id">
                    <a href="#">
                        #{{tag.name}}
                    </a>
                </span>
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
props: ['post'],


methods:{
    ValidURL(str) {
        var regex = /(?:https?):\/\/(\w+:?\w*)?(\S+)(:\d+)?(\/|\/([\w#!:.?+=&%!\-\/]))?/;
        if(!regex .test(str)) {
            return false;
        } else {
            return true;
        }
    } 
}
}
</script>

<style>

</style> 