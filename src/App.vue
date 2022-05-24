<template>
    <div class=" app">   
        <post-form @create = "createPost" />
        <post-list :posts="posts" @delete = "deletePost" /> 
    </div>
</template> 
<script>
import PostForm from "./components/PostForm";
import PostList from "./components/PostList";
import axios from 'axios';
export default{
    components:{
    PostList,
    PostForm
}, 
    data() {
        return{
            posts:[],
        }
    },
    mounted() {
        this.fetchPosts();
    },   
    methods:{
        deletePost(post){
            /*this.posts.splice(post);*/
            this.posts.splice(this.posts.indexOf(post), 1);
        },
        async fetchPosts() {
            try {
                const response = await axios.get('http://localhost:90/get/');
                this.posts = response.data;
            } catch (e) {
                alert(e);
            } finally {
                this.isPostsLoaded = true;
            }
        },
        createPost(post){
            //this.posts.push(post);
           /*  var param = {
                    id: post.id,
                    name: post.name,
                    phone: post.phone,
                    body: post.body   
            } */
           
            axios({
                method: 'post',
                headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
                url: 'http://localhost:90/add/',
                data: {
                    id: post.id,
                    name: post.name,
                    phone: post.phone,
                    body: post.body  
                }
            })
            .then(function(response) {

                console.log(response);

            })
            .catch(function (error) {
                console.log(error);
            });
/*
             try {
                 const response = axios.get('http://localhost:90/add/',JSON.stringify(param));
                this.posts = response.data;
            } catch (e) {
                alert(e);
            } finally {
                this.isPostsLoaded = true;
            } */
        }
    }
}
</script>
<style>
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
.app{
    padding: 20px;
}

</style>