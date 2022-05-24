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
                const response = await axios.get('http://localhost:90/add/');
                this.posts = response.data;
            } catch (e) {
                alert(e);
            } finally {
                this.isPostsLoaded = true;
            }
        },
        createPost(post){
            this.posts.push(post);
            var param = {
                    id: this.id,
                    name: this.name,
                    phone: this.phone,
                    body: this.body
    
            }
            axios.post( 
                ''
                , JSON.parse(JSON.stringify(param))
            )
            .then(function (response) {
                console.log(response.data);
            })
            .catch(function (error) {
                console.log(error);
            });
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