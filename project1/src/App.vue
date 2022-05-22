<template>
    <div class=" app">   
        <post-form @create = "createPost" />
        <post-list :posts="posts"  /> 
    </div>
</template> 
<script>
import PostForm from "./components/PostForm";
import PostList from "./components/PostList";
export default{
    components:{
    PostList,
    PostForm
},
    data() {
        return{
            posts:[
               {id:1, name: 'Тест Тостович', phone: '8 (800) 555 35-35', body: ' Банк'},
               {id:2, name: 'Илья Палыч', phone: '8 (800) 555 36-36', body: ' Щегол'},
               {id:3, name: 'Илья Палыч', phone: '8 (800) 555 36-36', body: ' Джун'}
            ],
        }
    },
    methods:{
        createPost(post){
            this.posts.push(post);
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